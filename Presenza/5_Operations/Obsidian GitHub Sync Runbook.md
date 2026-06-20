# Obsidian GitHub Sync Runbook

## Current Setup

- Actual Obsidian Vault: `/Users/maedayuuya/Desktop/Yuya`
- GitHub repository: `https://github.com/yuya918/yuya-vault`
- Branch: `main`
- Sync tool: Obsidian Git
- GitHub authentication: GitHub CLI (`gh auth login` and `gh auth setup-git`)

## What Happened

最初に、実際に使っている Obsidian Vault を確認する前に、別フォルダで仮の `daily-travel` リポジトリを作ってしまった。

本来GitHubへ載せるべきだったのは、Obsidianで実際に開いている `Yuya` Vault だった。

現在は `daily-travel` ではなく、`yuya-vault` を本命リポジトリとして使う。

## Lessons

- GitHub連携を始める前に、Obsidianの実Vaultパスを必ず確認する。
- Vaultとして使うフォルダは `.git` があるフォルダと一致させる。
- 仮リポジトリを先に作らず、実フォルダの中身を確認してからGitHubへpushする。
- GitHub認証は毎回トークンを貼らず、GitHub CLIで一度ログインして使う。
- Obsidian Gitの設定はUIで見つからない場合、`.obsidian/plugins/obsidian-git/data.json` を確認する。
- 認証補助ファイルやローカル作業状態はGitHubへ載せない。

## Daily Operation

通常はObsidianで編集するだけでよい。

Obsidian Git の自動同期設定:

- Auto commit interval: 10 minutes
- Auto pull interval: 5 minutes
- Pull on startup: enabled
- Pull before push: enabled
- Commit message: `vault: update {{date}}`

手動で同期したい場合:

```bash
cd /Users/maedayuuya/Desktop/Yuya
git status
git add .
git commit -m "vault: update"
git push
```

## Safety Checks

GitHubへpushできているか確認する:

```bash
cd /Users/maedayuuya/Desktop/Yuya
git status --short --branch
git log --oneline -5
```

正常な状態:

```text
## main...origin/main
```

`ahead 1` のように表示された場合は、ローカルに未pushのコミットがある。

## Do Not Use

古い仮リポジトリ:

```text
yuya918/daily-travel
```

今後は混乱を避けるため、Obsidianの本命Vaultとしては使わない。

