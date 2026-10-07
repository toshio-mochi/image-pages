# image-pages

GitHub Pages で画像・動画を公開するための最小構成例です。

## これは何ですか

このリポジトリは、プライベートリポジトリで GitHub Pages を使うための例として作成した最小構成です。

- `index.html` を Pages の公開ページとして使う
- `images/` に画像や動画を置く
- GitHub にログインしているユーザーのみアクセスできる状態を想定する
- `gh` CLI を使ってリポジトリのクローンや認証を行う方法を説明する

## GitHub Pages を有効化する手順

注: GitHub Pages は GitHub のリポジトリ設定で有効化します。リポジトリがプライベートでも、設定画面で有効化は可能です。ただし、通常は GitHub にログインした状態でアクセスできる公開ページになります。

### Web UI で有効化する

1. GitHub のリポジトリを開く
2. `Settings` を開く
3. 左メニューから `Pages` を選択
4. `Source` で `Deploy from a branch` を選択
5. `Branch` で `main` を選択
6. `/(root)` を選択
7. `Save` を押す

GitHub Pages の URL は、設定画面の `Visit site` または `Your site is live at ...` で確認できます。

### `gh` を使って設定する

GitHub CLI を使う場合は、まずログインします。

```bash
gh auth login
```

ログイン後、リポジトリをクローンします。

```bash
gh repo clone toshio-mochi/image-pages
cd image-pages
```

このリポジトリに対して GitHub Pages の設定自体は UI から行うのが確実ですが、CLI での認証やクローンは次のように使えます。

```bash
gh auth status
gh repo view toshio-mochi/image-pages
```

### プライベートリポジトリでアクセスする方法

プライベートリポジトリの GitHub Pages では、通常、GitHub にログイン済みでアクセス可能な形になります。

#### ログイン済みでアクセス

- GitHub でサインインした状態で Pages の URL を開く
- その URL に直接アクセスする

#### `gh` で使う

```bash
gh auth login
gh repo clone toshio-mochi/image-pages
```

#### PAT を使う場合

```bash
git clone https://YOUR_USERNAME:YOUR_PERSONAL_ACCESS_TOKEN@github.com/toshio-mochi/image-pages.git
```

注意: PAT は十分に管理し、必要最小限の権限で使用してください。

## このリポジトリの構成

```text
image-pages/
├── README.md
├── index.html
└── images/
    └── sample-image.svg
```

## 画像や動画を置く方法

`images/` フォルダにファイルを置いて、`index.html` から参照します。

### 画像の例

```html
<img src="images/sample-image.svg" alt="サンプル画像" />
```

### 動画の例

```html
<video controls width="640">
  <source src="images/sample-video.mp4" type="video/mp4" />
  お使いのブラウザは video タグをサポートしていません。
</video>
```

## ローカル確認方法

```bash
cd image-pages
python3 -m http.server 8000
```

ブラウザで以下を開きます。

```text
http://localhost:8000/
```

## 反映と更新

```bash
git add .
git commit -m "Add GitHub Pages sample"
git push origin main
```

## トラブルシューティング

### Pages が表示されない

- `Settings` > `Pages` で有効化されているか確認
- `main` ブランチが選択されているか確認
- `index.html` がルートにあるか確認
- 数分待ってから更新を再読み込みする

### プライベートリポジトリで見えない

- GitHub にログイン済みか確認
- 対象のユーザーがリポジトリにアクセス権限を持っているか確認
- Pages の URL はリポジトリごとに異なるので、設定画面で URL を確認

## 参考

- GitHub Docs: GitHub Pages
- GitHub CLI: `gh auth login`, `gh repo clone`

---
本リポジトリはサンプル構成です。必要に応じて、画像や動画を追加してページを拡張できます。
