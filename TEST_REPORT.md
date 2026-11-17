# STEP 11（v1.1）検証結果 — 2026-11-17

## 対象
- `volley_referee_step11_github_pages_v11.zip`（GitHub Pages用ファイル8点）
- `index.html` / `manifest.webmanifest` / `sw.js` / アプリアイコン

## 確認できたこと
- ZIP検査：OK。フォルダー最上位にHTML・Manifest・Service Worker・アイコン等が展開される
- JS構文検査：OK（Node.js v22 `node --check`：アプリ内スクリプト、`sw.js`）
- Manifest：形式・アプリアイコンサイズ・相対パス・起動URLを確認
- ChromiumのHTML挿入検証：6人制・9人制でセット開始→得点入力の画面更新を確認（844×390）
- 上記のUI検証でページJavaScriptの例外なし
- 画面はネット中心の横向き表示を維持。既存のサービス順・交代操作UIを維持

## 未確認・制限
- この実行環境ではChromiumによるローカルURLへのアクセスが管理ポリシーでブロックされるため、Service Worker登録、オフライン再起動、PWAインストールの**実動作検証は未実施**。
- ブラウザの `page.set_content` によるHTML挿入ではストレージのオリジンがないため、ローカル保存警告が出る。これは本来のHTTPS配信時の保存テストを代替しない。
- Android実機でのスリープ復帰・画面保持・長時間タイマーは未検証。
- GitHubリポジトリ作成およびPagesの有効化は未実施（公開URLは未発行）。

## 次の確認
1. 新規リポジトリへZIPを**展開して中身を**アップロードし、GitHub Pagesを `main / (root)` から公開
2. Android Chromeで公開URLを開き、ホーム画面から起動
3. 一度オンラインで開いた後、機内モードにしてオフライン起動を確認
4. 試合操作と保存復元、画面保持、30秒／3分計測を実機チェック票で確認

試作版のため、公式審判業務では記録用紙・競技規則・大会特別規則を優先する。
