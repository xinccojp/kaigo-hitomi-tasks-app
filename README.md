# ビジネス課題ボード — アプリ殻（public）

「介護のひとみさん」ビジネス課題ボードの**フロント（単一HTML）だけ**を置く public リポジトリ。
GitHub Pages で配信する。**このリポジトリにはタスクデータも秘密情報も含まない**（殻のみ）。

- 課題データの実体（`tasks/*.md`）は **private リポジトリ `xinccojp/kaigo-hitomi-tasks`** にある。
- 本アプリは実行時に、利用者個人の PAT で private データリポジトリの GitHub Contents API を叩いて読み書きする。
- したがって Pages が public でも、**データは PAT を持つ人にしか見えない**（漏洩しない）。

## 使い方（チームメンバー）
1. Pages URL を開く: `https://xinccojp.github.io/kaigo-hitomi-tasks-app/`
2. 右上「トークン設定」で **fine-grained PAT** を入力。
   - 対象リポジトリ: `xinccojp/kaigo-hitomi-tasks`（**private データ側**）
   - 権限: **Contents: Read and write**
   - PAT はブラウザの localStorage にのみ保存。GitHub API へのみ送信。
3. タスクの作成・編集・状態変更が、private データリポジトリの `tasks/*.md` への commit になる。

## 設定
データリポジトリの指定は `index.html` 冒頭の `REPO` 定数（`owner/repo/branch/dir`）。env var は使わない。
データ形式の詳細は private データリポジトリの README を参照。
