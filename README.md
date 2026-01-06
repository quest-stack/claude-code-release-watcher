# Claude Code Release Watcher 🚀

Claude Codeの新しいリリースを自動監視し、Slackに通知するGitHub Actionsワークフローです。

## 機能

- ⏰ 毎日9:00 JST に自動チェック
- 📢 新しいリリースがあればSlackに通知
- ⭐ MCP / Tool Search 関連の更新を自動ハイライト
- 🔄 手動実行も可能

## セットアップ

### 1. Slack Webhook URLの設定

1. リポジトリの **Settings** → **Secrets and variables** → **Actions** へ移動
2. **New repository secret** をクリック
3. 以下を入力:
   - Name: `SLACK_WEBHOOK_URL`
   - Secret: `https://hooks.slack.com/services/...` （あなたのWebhook URL）
4. **Add secret** をクリック

### 2. 手動テスト

1. **Actions** タブを開く
2. **Check Claude Code Releases** を選択
3. **Run workflow** をクリック

## 通知サンプル

```
🚀 Claude Code v1.0.50 がリリースされました！

リリース日時: 2026-01-06T10:00:00Z
詳細: GitHub Release Page

⭐ 注目: MCP/Tool Search関連の更新が含まれている可能性があります！

変更内容:
- Tool Search Tool のサポートを追加
- パフォーマンス改善
- バグ修正
```

## 監視対象

- リポジトリ: [anthropics/claude-code](https://github.com/anthropics/claude-code)
- 対象: GitHub Releases

## カスタマイズ

### チェック頻度の変更

`.github/workflows/check-releases.yml` の `cron` を変更:

```yaml
on:
  schedule:
    # 毎日9:00と21:00 JSTに実行（1日2回）
    - cron: '0 0,12 * * *'
```

### 通知チャンネルの変更

ワークフロー内の `channel` を変更:

```json
"channel": "#your-channel-name"
```

## License

MIT
