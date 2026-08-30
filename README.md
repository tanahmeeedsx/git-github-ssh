# Git & GitHub SSH Practice

A hands-on practice repository for learning Git, GitHub, SSH authentication, branching, commits, and remote repository management.

---

## 🔐 GitHub SSH Authentication

SSH allows Git to securely communicate with GitHub without entering a GitHub username and password for every push or pull.

### 1. Generate an SSH Key

An ED25519 SSH key was generated using:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

This creates two files:

```text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

* `id_ed25519` → Private key. **Never share this file.**
* `id_ed25519.pub` → Public key. This is added to GitHub.

### 2. Add the Public Key to GitHub

Display the public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output and add it to:

**GitHub → Settings → SSH and GPG keys → New SSH key**

### 3. Test SSH Authentication

After adding the public key to GitHub:

```bash
ssh -T git@github.com
```

A successful authentication returns a message similar to:

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### 4. Clone a Repository Using SSH

Instead of using HTTPS:

```bash
https://github.com/username/repository.git
```

use the SSH URL:

```bash
git@github.com:username/repository.git
```

Example:

```bash
git clone git@github.com:tanahmeeedsx/git-github-ssh.git
```

### 5. Verify the Remote

Inside the repository:

```bash
git remote -v
```

Expected:

```text
origin  git@github.com:tanahmeeedsx/git-github-ssh.git (fetch)
origin  git@github.com:tanahmeeedsx/git-github-ssh.git (push)
```

### 6. Push Changes Using SSH

After making changes:

```bash
git status
git add .
git commit -m "Update README"
git push
```

GitHub authenticates the connection using the SSH key configured on the local machine.

---

## 🔄 SSH Git Workflow

```text
Local Repository
       │
       │ git push
       ▼
    SSH Key
       │
       │ Authentication
       ▼
     GitHub
       │
       ▼
Remote Repository
```

### HTTPS vs SSH

| HTTPS                                        | SSH                               |
| -------------------------------------------- | --------------------------------- |
| Uses HTTPS remote URL                        | Uses SSH remote URL               |
| Authentication may require credentials/token | Uses SSH key authentication       |
| Example: `https://github.com/...`            | Example: `git@github.com:...`     |
| Easy to start with                           | Convenient for regular Git use    |
| Credentials/token management                 | Public/private key authentication |

---

## 📚 Git Daily Commands Cheatsheet

### 🔁 The Standard Daily Workflow

Use these commands continuously to track and save your progress.

* `git status`

  * Shows modified, staged, or untracked files.
* `git add .`

  * Stages all current changes.
* `git add <file-name>`

  * Stages a specific file.
* `git commit -m "your descriptive message"`

  * Saves staged changes into local Git history.

### 🔀 Branching & Feature Management

* `git branch`

  * Lists local branches.
* `git switch -c <new-branch-name>`

  * Creates and switches to a new branch.
* `git switch <branch-name>`

  * Switches to an existing branch.
* `git merge <branch-name>`

  * Merges another branch into the current branch.

### 🌐 Remote Repository

* `git clone <ssh-url>`

  * Clones a repository using SSH.
* `git pull`

  * Downloads and merges remote changes.
* `git pull --rebase`

  * Downloads changes and rebases local commits on top.
* `git push`

  * Uploads local commits to the remote repository.
* `git push -u origin <branch-name>`

  * Pushes a new branch and sets its upstream.
* `git fetch`

  * Downloads remote changes without modifying the working directory.

### 🔍 Inspecting Changes & History

* `git diff`

  * Shows unstaged changes.
* `git diff --staged`

  * Shows staged changes.
* `git log --oneline --graph`

  * Displays a visual commit history.

### 🛠️ Handling Interruptions & Mistakes

* `git stash`

  * Temporarily stores uncommitted changes.
* `git stash pop`

  * Restores the latest stash.
* `git commit --amend -m "updated message"`

  * Updates the latest commit.
* `git restore <file-name>`

  * Discards unstaged changes to a file.
  * 
## Pull Practice

Testing git pull from GitHub to local machine.
