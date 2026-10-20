# Baccarat Intelligence Console — アプリとしてインストールする（自分専用）

このフォルダは PWA（ホーム画面アプリ）一式です。`index.html` / `manifest.webmanifest` / `sw.js` / `icons/` を **HTTPS で配信されるどこか**に置くと、iPhone・iPad・MacBook にアプリとして入ります。一度入れればオフラインで動きます。

## 1. ホスティング（1回だけ・5分）

### A. GitHub Pages（推奨・無料）
1. GitHub で新しいリポジトリ `baccarat-console` を作成（Public。中身はゲームのコードのみで個人データは含まれません）
2. このフォルダの中身（`index.html`, `manifest.webmanifest`, `sw.js`, `icons/`）をリポジトリ直下にアップロード
3. Settings → Pages → Source: `Deploy from a branch` / Branch: `main` / `/ (root)` → Save
4. 1〜2分後に `https://<ユーザー名>.github.io/baccarat-console/` が開けるようになる

### B. 他の静的ホスティング
Cloudflare Pages / Netlify / Vercel のいずれでも、このフォルダをドラッグ＆ドロップするだけで同じく動きます。

## 2. 端末にインストール

| 端末 | 手順 |
|---|---|
| iPhone / iPad（Safari） | 上の URL を開く → 共有ボタン → **ホーム画面に追加** → 追加。ホーム画面のアイコンから全画面で起動 |
| MacBook（Safari 17 以降） | URL を開く → ファイル → **Dock に追加**。独立したアプリとして Dock から起動 |
| MacBook（Chrome / Edge） | URL バー右端のインストールアイコン → インストール |

## 3. 端末間の同期（自分専用クラウド）

アプリ版は GitHub の「秘密の Gist」を自分専用クラウドとして使います。

1. GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained token** → Permissions で **Gists: Read and write** のみ → Generate
2. 最初の端末: アプリの 設定 → Sync → Token を貼る → 数秒で Gist ID が自動作成され表示される
3. 他の端末: 同じ Token と、表示された Gist ID を貼る → 続きが読み込まれる

以後は自動で同期（変更の2秒後に保存、画面を開いたとき・30秒ごとに取得）。片方ずつ使ってください（同時に遊ぶと後に保存した方が優先）。

- トークンは各端末の中にだけ保存され、Gist にも claude.ai にも送られません
- claude.ai のアーティファクト版は Gist 不要で、ログインだけで同期します

## 4. 更新
新しい `index.html` / `sw.js` をホスティングに上げると、次回起動時に「新しいバージョンがあります → 再読込」と出ます。

## 5. バックアップ
設定 → Data → JSON を表示 → コピー。Obsidian 等に貼っておけば、端末を失っても「インポート」で全履歴が戻ります。
