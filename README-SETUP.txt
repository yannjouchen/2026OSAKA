GitHub Actions 版 USJ 即時排隊設定
================================

這個版本不再讓 Safari 直接呼叫 Queue-Times API。
流程：

Queue-Times → GitHub Actions → usj-queue.json → GitHub Pages → Safari

需要放到 repo 的檔案
-------------------
1. index.html
2. usj-queue.json
3. .github/workflows/usj-queue-pages.yml

第一次設定
----------
1. 把上面三個檔案放到 yannjouchen.github.io 的 repo，commit 到 main。
2. GitHub repo → Settings → Pages。
3. Build and deployment → Source 改成「GitHub Actions」。
4. 到 repo 的 Actions 頁面。
5. 打開「USJ Queue → Deploy Pages」。
6. 按 Run workflow，選 main，執行一次。
7. 等 workflow 的 build + deploy 都變綠色。
8. 重新整理 https://yannjouchen.github.io/ ，切到 Day 3。
9. 「USJ 即時排隊看板」應會顯示 usj-queue.json 的資料。

自動排程
--------
已設定 2026/10/11 日本時間約 06:00～22:55，每 5 分鐘嘗試更新。
GitHub 的 schedule 並不保證準時，可能會延遲。

為什麼不每 5 分鐘 commit？
------------------------
這版使用 GitHub Pages artifact 部署，不會為了排隊資料每 5 分鐘在 main 製造一個新 commit。

測試時
------
任何時間都可到 Actions → USJ Queue → Deploy Pages → Run workflow 手動執行。

現場注意
--------
Queue-Times 是第三方資料。
Super Nintendo World 區域入場券、臨時停駛與最終等待時間仍以 USJ 官方 App 為準。

Day 3 活動場次同步（v38）
-----------------------
Day 3 的 ONE PIECE PREMIER SHOW、Wicked、NO LIMIT! 遊行與萬聖節街頭／舞台內容，
會讀取同一份 2026/10/11 USJ 官方 Show Schedule：
- 尚未公布：卡片顯示「等待 USJ 公布」
- 已公布且有場次：卡片直接顯示當日實際時間
- 已公布但沒有該活動：卡片顯示「10/11 無演出／未排定」

芙莉蓮 Story Walk 不是定時演出；卡片顯示 10:00～閉園，閉園時間公布後會自動補成實際時間。
4-D／恐怖屋／整理券體驗屬非定時演出，不會誤套 Show Schedule 場次。
