# WakaTime セットアップガイド

このガイドに従って、GitHubプロフィールにWakaTimeの統計情報を表示できます。

## 📋 必要な準備

### 1. WakaTimeアカウントの作成

1. [WakaTime](https://wakatime.com/)にアクセス
2. 「Sign up」をクリック（GitHub連携が便利です）
3. アカウントを作成

### 2. エディタにWakaTime拡張機能をインストール

#### Visual Studio Code の場合
1. VSCodeの拡張機能タブを開く
2. "WakaTime"で検索
3. 「WakaTime」拡張機能をインストール
4. インストール後、WakaTime API Keyの入力を求められます

#### その他のエディタ
- [WakaTime Plugins](https://wakatime.com/plugins)から対応エディタを選択

### 3. WakaTime API Key の取得

1. [WakaTime Settings](https://wakatime.com/settings/account)にアクセス
2. 「Secret API Key」をコピー
3. エディタの設定に貼り付け

### 4. GitHub Secrets の設定

1. このリポジトリ（`qua121-qua121`）の「Settings」タブを開く
2. 左サイドバーから「Secrets and variables」→「Actions」を選択
3. 「New repository secret」をクリック

#### 必要なSecret (2つ)

**Secret 1: WAKATIME_API_KEY**
- Name: `WAKATIME_API_KEY`
- Value: WakaTimeからコピーしたAPI Key

**Secret 2: GH_TOKEN**
- Name: `GH_TOKEN`
- Value: GitHub Personal Access Token（以下の手順で作成）

### 5. GitHub Personal Access Token の作成

1. GitHubの「Settings」→「Developer settings」→「Personal access tokens」→「Tokens (classic)」
2. 「Generate new token」→「Generate new token (classic)」を選択
3. 以下の設定で作成：
   - Note: `WakaTime Readme Stats`
   - Expiration: `No expiration`（または適切な期限）
   - Scopes: `repo`（チェックを入れる）
4. 生成されたトークンをコピーして、上記の`GH_TOKEN`に設定

### 6. README.md の更新

`README.md`内のWakaTimeセクションのコメントアウトを解除します：

1. 以下の部分を探す：
```markdown
<!--
## ⏱️ Coding Time (WakaTime)
...
-->
```

2. コメントを削除して有効化：
```markdown
## ⏱️ Coding Time (WakaTime)

<div align="center">

<!--START_SECTION:waka-->
<!--END_SECTION:waka-->

</div>
```

### 7. GitHub Actions の有効化

1. リポジトリの「Actions」タブを開く
2. 「I understand my workflows, go ahead and enable them」をクリック
3. 左サイドバーから「Waka Readme」ワークフローを選択
4. 「Run workflow」をクリックして手動実行

## ✅ 確認

- エディタでコーディングを開始すると、WakaTimeが自動的に時間を記録
- 24時間後、GitHub Actionsが自動実行されREADMEに統計が追加される
- 毎日午前0時（UTC）に自動更新される

## 🔧 トラブルシューティング

### GitHub Actionsがエラーになる場合
- `WAKATIME_API_KEY`と`GH_TOKEN`が正しく設定されているか確認
- トークンに`repo`のスコープが付与されているか確認

### 統計が表示されない場合
- WakaTimeでコーディング時間が記録されているか確認
- 最低7日間のデータが必要な場合があります

## 📚 参考リンク

- [WakaTime 公式サイト](https://wakatime.com/)
- [waka-readme-stats GitHubリポジトリ](https://github.com/anmol098/waka-readme-stats)
- [WakaTime Plugins](https://wakatime.com/plugins)
