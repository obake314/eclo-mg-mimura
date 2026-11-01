# testweb4 自動デプロイ

mainへのPush、またはActionsの「Deploy to Lolipop」→「Run workflow」で実行します。

- URL: https://testweb4.elegirl.net/
- SSH: ciao.jp-elegirl@ssh.lolipop.jp:2222
- 配置先: /home/users/0/ciao.jp-elegirl/web/testweb4/

## 最初の設定

GitHubリポジトリの Settings → Secrets and variables → Actions → New repository secret で登録します。

- Name: LOLIPOP_SSH_PASSWORD
- Secret: ロリポップのSSHパスワード

パスワードをファイルやチャットには記載しないでください。登録後、Actionsから初回実行します。

## 反映範囲

Git管理下のWordPress本体・テーマ・プラグインのコードを反映します。
データベース、画像、wp-config.php、.htaccess、バックアップ、キャッシュ、有料移行拡張は反映しません。
サーバーだけに存在するファイルは削除しません。コードの上書きは行われます。
既存のWordPress（wp-config.php）とrsyncが配置先サーバーにない場合は停止します。
投稿・設定・サイトエディターの変更などデータベース内の内容は、この方法では移行されません。

## バックアップ

上書きされる旧ファイルは、公開フォルダの外の以下へ保存されます。
/home/users/0/ciao.jp-elegirl/deploy-backups/mimura/<実行ID>-<再実行回数>/

必要に応じて古いバックアップを整理してください。失敗時の自動ロールバックはありません。

## サーバー確認

同梱のSSHホスト鍵は、ロリポップ公式ヘルプ掲載のRSA fingerprint
SHA256:1Rt0rvYV+xZGCMAzm6BKjqAIPWXYYDX0bYK5CikAvCE と照合済みです。
https://support.lolipop.jp/hc/ja/articles/360048379614

ホスト鍵が変更された場合は検証で停止します。公式情報で確認してから更新します。
