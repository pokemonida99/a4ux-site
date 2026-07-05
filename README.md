# A4UX 不想上班影業 — 頻道形象網站

一夜生成的電影等級頻道網站 + 數據健檢報告。

## 內容

| 檔案 | 說明 |
|---|---|
| `index.html` | 公開形象網站（片頭動畫、海報牆、票房排行、頻道編年史） |
| `insights.html` | **老闆專用**：觀看數下滑診斷 + 6 帖處方（不要公開這頁） |
| `data.js` | 全頻道 135 部公開影片資料（標題/觀看/讚/日期/分類/主色） |
| `thumbs/` | 原尺寸封面 138 張（最高畫質） |
| `thumbs_s/` | 480px 縮圖（網頁用） |
| `avatar.png` | 頻道頭像 |

## 本機預覽

```bash
cd a4ux-site
python3 -m http.server 8642
# 開 http://localhost:8642
```

直接雙擊 `index.html` 也能看（字型需要網路）。

## 部署

整個資料夾丟到任何靜態空間即可：Netlify / Vercel / GitHub Pages / Cloudflare Pages。
部署前建議把 `insights.html` 移出資料夾（那是內部報告）。

## 更新資料

影片資料由 yt-dlp 抓取（2026-07-06 快照）。之後要更新：
1. `yt-dlp --flat-playlist -J "https://www.youtube.com/@a4ux/videos"` 取得影片清單
2. 逐部抓 metadata、下載新封面到 `thumbs/`、縮圖到 `thumbs_s/`
3. 重新產生 `data.js`（格式見檔案開頭）

會員專屬影片（3 部）無法公開抓取，不在統計內。
