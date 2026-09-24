# ツーリズムEXPO 2026 体験ガイド（非公式）

ツーリズムEXPOジャパン2026 一般公開日（9/26・27）向けの非公式ガイド。1ファイルの静的サイトで、GitHub Pages にそのまま置けます。

- `index.html` … サイト本体（データもすべてこの中）
- `og.png` … Xなどでシェアされたときのカード画像（1200×630）
- `.nojekyll` … GitHub Pages に Jekyll 処理をさせないための空ファイル

## 公開手順

1. GitHub で新しいリポジトリを作る（`tej-guide` 組織に `tej2026`、Public）。README などは追加せず空のまま。
2. Mac のターミナルで：

   ```sh
   cd ~/workspace/tej2026-guide
   # シェア用URLを自分のものに置き換え（<USER> を GitHub のユーザー名に）
   sed -i '' 's#%%SITE_URL%%#https://tej-guide.github.io/tej2026/#g' index.html
   git init
   git add .
   git commit -m "TEJ2026 guide"
   git branch -M main
   git remote add origin https://github.com/tej-guide/tej2026.git
   git push -u origin main
   ```

3. GitHub のリポジトリ → Settings → Pages → Source を「Deploy from a branch」、Branch を `main` / `/ (root)` にして Save。
   1〜2分後に `https://tej-guide.github.io/tej2026/` で公開されます。

## アフィリエイトの設定

`index.html` の末尾近くにある `const SITE = {...}` に、各サービスで発行したリンクを貼ります。

```js
const SITE = {
  aff: {
    rakuten: "https://hb.afl.rakuten.co.jp/...",  // 楽天トラベル
    jalan:   "https://ck.jp.ap.valuecommerce.com/...", // じゃらん
    veltra:  "https://www.veltra.com/jp/...?..."   // ベルトラ
  },
  tip: "https://ofuse.me/..."   // 投げ銭（任意）
};
```

- どれか1つでも入れると、ページ最上部に「本ページはアフィリエイト広告を利用しています」が自動で表示され、該当ボタンに「広告」ラベルと `rel="sponsored"` が付きます。空のままなら通常のリンクです。
- 2023年10月からのステルスマーケティング規制（景品表示法）により、アフィリエイトを含むページには広告であることの表示が必要です。この自動表示を消さないでください。
- 各アフィリエイトの対象商品・規約（入場券が報酬対象か、など）は各サービスで確認してください。

## 注意

- 主催者・出展者とは無関係の非公式ページです。公式ロゴは使っていません。
- 本文中の「PR」ラベルは「プレスリリースが情報源」という意味です。広告の意味ではありません。
- 最新情報欄は `index.html` の `const NEWS = [];` に `[時刻, GATE, 見出し, 本文, X投稿URL]` を追加すると表示されます。
