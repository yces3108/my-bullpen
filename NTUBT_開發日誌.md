# 台大棒球隊練球日程表 開發日誌
終於要來開始架設網頁了！  
這個頁面預計會有下面幾種功能：  
* 隊員名單管理
* 練球日程表（小練、重訓、大練、比賽、裁判）
* （隊長）球隊訓練日程安排
* 裁判日程填單
* （負責人）訓練進度管理
* （經理）共用資料區
* 部落格
* 影片上傳連結
## 架構發想
我需要創設哪些類別（class）、元件（component）、服務（service）？  
之後想辦法畫成樹狀圖好了。
### 類別
* 隊員（資料、個人練球時段）
* 時段項目（練球、站裁判、比賽）與成員
* 文章或訊息
### 元件
* 登入頁面
* 日程表
* 單日日程
* 日程安排表
* 訓練管理頁
* 共享資源頁
* 部落格
## 設定路由
一開始當然是生成專案，

    ng new NTUBT --routing
後面要幫它增加module和component，要這樣做：  

    ng generate module home --routing
    ng generate component home
    等等
如果一個module裡面用到很多UI元件，那都要一一寫入！晚點再加上。
接著要在app-routing.module.ts裡面改這個，

    import { NgModule } from '@angular/core';
    import { Routes, RouterModule, PreloadAllModules } from '@angular/router'; // import進來第三個預先導入的功能！
    import { appPath } from './app-path.const'; // 去寫一個Constant檔！

    const routes: Routes = [
      {
        path: appPath.home,
        //loadChildren: './home/home.module#HomeModule' // 好像不能這樣寫，要寫成下面這樣
        loadChildren: () => import('./home/home.module').then(mod => mod.HomeModule)
      },...
    }
    @NgModule({
      imports: [RouterModule.forRoot(routes, {
        preloadingStrategy: PreloadAllModules // 這個要在上面先導入
      })],
      exports: [RouterModule]
    })
    export class AppRoutingModule { }
## CSS垂直置中
https://pjchender.blogspot.com/2015/04/css_15.html  
## 終於來到我的第一次上傳！
如何將本地vue項目上傳到github  
https://www.twblogs.net/a/5d00cc21bd9eee14644f862d  
如何處理 Webpack 打包後空白頁面處理  
https://medium.com/@happyjayxin/vue-npm-run-build-%E7%A9%BA%E7%99%BD%E8%A7%A3%E6%B1%BA-4cbecb87e643  
Vuejs部屬GitHub Pages(包含上傳檔案和page，很完整)  
https://hsiangfeng.github.io/vue/20190513/948497494/  
## 為什麼重新整理之後，就會跑回到404？
淺談新手在學習 SPA 時的常見問題：以 Router 為例  
https://github.com/aszx87410/blog/issues/48  
這個觀念實在重要！  
[IT 鐵人賽] Router 基本入門 Day 9 (內有萬用匹配設定方法)  
https://blog.hinablue.me/2019-ithome-ironman-day-9/  
Vue Router  
https://medium.com/@linwei5316/vue-router-4c2aad1cc352  
## 有用到cookie的註冊登錄頁面
https://segmentfault.com/a/1190000009329619
## 整合Vue前端與Django後端
整合 Django + Vue.js 框架快速搭建web项目  
https://cloud.tencent.com/developer/article/1005607  
Django+Vue.js构建项目(這個更精采)  
https://zhuanlan.zhihu.com/p/54776124  
原來是Vue把MVVM的Model部分交給Django，Django把MVC的View交給Vue，中間的AJAX用axios來達成。  
2小时入门Django(DRF)+Vue·前后端分离简明指南  
https://blog.cyru1s.com/posts/Django-vue.html  
Django： django-cors-headers 报错 no module named "corsheaders" (參考一下)  
https://www.cnblogs.com/2012-dream/p/10529228.html  
(看情況是要pip install django-cors-headers還是pipenv install django-cors-headers解決)  
Django2与@Vue/Cli3整合--访问静态文件404问题 (最後是這篇真的解決問題！)  
https://blog.csdn.net/Amio_/article/details/88354438  
axios安装 使用及如何解决‘axios  is not defined’  
https://blog.csdn.net/yytIcon/article/details/90713049  
Simple Movies web app with Vue, Vuetify and Django.  
https://medium.com/@samy_raps/simple-movies-web-app-with-vue-vuetify-and-django-part-1-setup-6351c02327a5

## 雜項
美按鈕！  
https://codepen.io/kathykato/full/rZRaNe  
https://uicookies.com/css-buttons/
