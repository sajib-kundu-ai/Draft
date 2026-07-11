# GitHub Repository তৈরি করে VS Code দিয়ে Commit & Push করার Beginner Guide

এই guide-টি beginnerদের জন্য। এখানে example project হিসেবে **Student-Portfolio** ব্যবহার করা হয়েছে।

---

## 1. Git, GitHub, VS Code — Basic ধারণা

### Git কী?

Git হলো একটি **version control system**।  
মানে তুমি project-এর code পরিবর্তন করলে Git সেই পরিবর্তনের history রাখে।

Example:

- আজ তুমি homepage তৈরি করলে
- কাল contact form add করলে
- পরশু একটা bug fix করলে

Git থাকলে তুমি চাইলে আগের version-এ ফিরে যেতে পারবে।

---

### GitHub কী?

GitHub হলো online platform যেখানে Git project/repository রাখা যায়।

তোমার local PC-এর project GitHub-এ push করলে:

- online backup থাকে
- অন্য device থেকে code পাওয়া যায়
- team memberদের সাথে কাজ করা যায়
- project portfolio হিসেবে share করা যায়

---

### VS Code কীভাবে help করে?

VS Code-এর **Source Control** panel দিয়ে terminal command ছাড়াও তুমি করতে পারো:

- changed files দেখা
- file stage করা
- commit করা
- GitHub-এ push করা
- GitHub থেকে pull করা

Shortcut:

```text
Ctrl + Shift + G
```

---

## 2. Important Terms

### Repository / Repo

Git দিয়ে track করা project folder-কে repository বা repo বলে।

Example:

```text
Student-Portfolio
```

---

### Commit

Commit হলো project-এর একটা saved checkpoint।

Example commit message:

```text
fix: update contact form validation
```

মানে এই commit-এ contact form validation fix করা হয়েছে।

---

### Stage

Commit করার আগে কোন file commit করবে সেটা select করা লাগে।  
এই select করাকেই **stage** বলে।

---

### Push

Local PC থেকে GitHub-এ commit upload করাকে **push** বলে।

---

### Pull

GitHub থেকে latest code local PC-তে আনা হলো **pull**।

---

### Remote

Local project-এর সাথে GitHub repository link connect করা হয় remote হিসেবে।

Example:

```text
origin https://github.com/username/student-portfolio.git
```

---

## 3. Full Workflow Overview

```text
Local Project Folder
        ↓
Git Initialize
        ↓
GitHub Repo Create
        ↓
Remote Connect
        ↓
Stage Files
        ↓
Commit
        ↓
Push to GitHub
```

---

## 4. Git Install আছে কিনা Check

Ubuntu terminal খুলে লিখো:

```bash
git --version
```

যদি version দেখায়, তাহলে Git installed আছে।

Git না থাকলে:

```bash
sudo apt update
sudo apt install git
```

---

## 5. Git User Name এবং Email Set করা

প্রথমবার Git setup করার সময় name এবং email দিতে হয়।

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Example:

```bash
git config --global user.name "Rahim Ahmed"
git config --global user.email "rahim@example.com"
```

Check করতে:

```bash
git config --global --list
```

Expected output:

```text
user.name=Rahim Ahmed
user.email=rahim@example.com
```

---

## 6. GitHub এ New Repository তৈরি

1. GitHub এ login করো
2. Top-right `+` icon চাপো
3. `New repository` select করো
4. Repository name দাও

Example:

```text
student-portfolio
```

5. Public অথবা Private select করো
6. Existing local project upload করতে চাইলে এগুলো unchecked রাখো:

```text
Add README file ❌
Add .gitignore ❌
Choose a license ❌
```

7. `Create repository` চাপো

---

## 7. Local Project Git দিয়ে Initialize করা

ধরি project folder:

```text
~/Student-Portfolio
```

Terminal:

```bash
cd ~/Student-Portfolio
```

Git initialize করো:

```bash
git init
```

Branch name `main` করো:

```bash
git branch -M main
```

---

## 8. GitHub Repo Local Project-এর সাথে Connect করা

GitHub repository link copy করো।

Example:

```text
https://github.com/username/student-portfolio.git
```

তারপর terminal এ:

```bash
git remote add origin https://github.com/username/student-portfolio.git
```

Remote ঠিকমতো add হয়েছে কিনা check:

```bash
git remote -v
```

Expected output:

```text
origin  https://github.com/username/student-portfolio.git (fetch)
origin  https://github.com/username/student-portfolio.git (push)
```

---

## 9. `.gitignore` তৈরি করা

`.gitignore` file বলে দেয় কোন file/folder GitHub-এ যাবে না।

Project root এ:

```bash
touch .gitignore
```

Example `.gitignore`:

```gitignore
# Environment files
.env
.env.local

# Node.js
node_modules/
dist/
build/

# Python
.venv/
__pycache__/
*.pyc

# Database
*.db

# Editor / OS
.vscode/
.DS_Store

# Logs
*.log
```

Important: কখনো API key, password, `.env`, database GitHub এ push করবে না।

---

## 10. First Commit করা

Status দেখো:

```bash
git status
```

সব file stage করো:

```bash
git add .
```

Commit করো:

```bash
git commit -m "Initial commit"
```

GitHub এ push করো:

```bash
git push -u origin main
```

এখন GitHub repository refresh করলে code দেখতে পাবে।

---

## 11. VS Code দিয়ে Project Open করা

Terminal থেকে:

```bash
cd ~/Student-Portfolio
code .
```

অথবা:

```text
VS Code → File → Open Folder → Student-Portfolio
```

---

## 12. VS Code Source Control ব্যবহার

VS Code এর left sidebar এ Source Control icon আছে।  
Shortcut:

```text
Ctrl + Shift + G
```

এখানে changed files দেখা যায়।

Example:

```text
M index.html
M styles.css
```

`M` মানে modified।

---

## 13. VS Code দিয়ে Stage করা

Source Control panel এ প্রতিটা changed file-এর পাশে `+` icon থাকবে।

একটা file commit করতে চাইলে শুধু ওই file-এর পাশে `+` চাপো।

Example:

```text
index.html
```

এটা stage করলে শুধু এই file commit হবে।

সব file একসাথে stage করতে চাইলে উপরের বড় `+` চাপা যায়, কিন্তু beginnerদের জন্য file বুঝে বুঝে stage করা ভালো।

---

## 14. VS Code দিয়ে Commit করা

Source Control panel এর message box এ commit message লিখো।

Example:

```text
fix: update homepage layout
```

তারপর `Commit` button চাপো।

ভালো commit message structure:

```text
type: short message
```

Common type:

```text
feat: নতুন feature
fix: bug fix
chore: config/package update
style: UI/design polish
docs: documentation update
refactor: code structure improve
```

Example:

```text
feat: add contact section
fix: improve mobile navbar
style: polish homepage design
docs: add setup guide
```

---

## 15. VS Code দিয়ে Push করা

Commit করার পর Source Control panel এ `Sync Changes` বা `Push` button দেখাবে।

Click করো:

```text
Sync Changes
```

এতে local commit GitHub এ upload হবে।

---

## 16. Daily VS Code Git Workflow

প্রতিদিন কাজ করার সময় এই flow follow করো:

```text
1. VS Code open
2. Code change
3. Project run/test
4. Source Control open
5. Changed files check
6. Specific files stage
7. Commit message write
8. Commit
9. Push / Sync Changes
```

---

## 17. Terminal দিয়ে Same কাজ করার Commands

Status:

```bash
git status --short
```

Specific file add:

```bash
git add index.html
```

Commit:

```bash
git commit -m "fix: update homepage layout"
```

Push:

```bash
git push
```

---

## 18. আলাদা আলাদা Commit করার ভালো Practice

এক commit এ সব file না দিয়ে কাজ অনুযায়ী আলাদা commit করা ভালো।

Example:

### Homepage update

```bash
git add index.html
git commit -m "feat: add homepage hero section"
git push
```

### CSS design update

```bash
git add styles.css
git commit -m "style: polish homepage design"
git push
```

### JavaScript bug fix

```bash
git add script.js
git commit -m "fix: correct menu toggle behavior"
git push
```

এতে পরে বুঝতে সহজ হয় কোন commit এ কী change করা হয়েছে।

---

## 19. Pull কীভাবে করবে

GitHub এ অন্য জায়গা থেকে change হলে local PC তে আনতে হয়।

Terminal:

```bash
git pull
```

VS Code:

```text
Source Control → Three dots menu → Pull
```

Push করার আগে মাঝে মাঝে pull করা ভালো:

```bash
git pull
git push
```

---

## 20. Conflict হলে কী করবে

Conflict হয় যখন একই file local আর GitHub—দুই জায়গায় আলাদা change থাকে।

VS Code file open করলে এমন option দেখাবে:

```text
Accept Current Change
Accept Incoming Change
Accept Both Changes
```

Meaning:

```text
Current = তোমার local code
Incoming = GitHub থেকে আসা code
Both = দুইটাই রাখবে
```

Resolve করার পর:

```bash
git add file-name
git commit -m "fix: resolve merge conflict"
git push
```

---

## 21. Last Commit Undo করার Basic Rules

### শুধু last commit undo, কিন্তু code থাকবে

```bash
git reset --soft HEAD~1
```

### last commit + code change দুটোই remove

```bash
git reset --hard HEAD~1
```

### GitHub এর last pushed version এ ফিরতে

```bash
git fetch origin
git reset --hard origin/main
git clean -fd
```

Warning: `reset --hard` দিলে uncommitted change delete হয়ে যাবে।

---

## 22. Backup Branch তৈরি

Risky change করার আগে backup branch বানাও:

```bash
git branch backup-before-big-change
```

Backup branch list দেখতে:

```bash
git branch
```

Backup branch এ যেতে:

```bash
git checkout backup-before-big-change
```

Main branch এ ফিরতে:

```bash
git checkout main
```

---

## 23. Safe Commit Checklist

Commit করার আগে:

```bash
git status --short
```

এইগুলো commit করা যাবে না:

```text
.env
.env.local
.venv/
node_modules/
dist/
build/
.next/
*.db
API key
password
secret token
raw dataset
```

---

## 24. Local Run Before Commit

Project type অনুযায়ী command ভিন্ন হতে পারে।

### HTML/CSS/JS project

Browser এ `index.html` open করে test করো।

### Node.js project

```bash
npm install
npm run dev
npm run build
```

### Python project

```bash
python --version
python main.py
```

### React / Next.js project

```bash
npm install
npm run dev
npm run build
```

---

## 25. Complete Beginner Example

ধরি তুমি `index.html` fix করেছো।

### Step 1: Status দেখো

```bash
git status --short
```

Output:

```text
M index.html
```

### Step 2: Test করো

Browser এ project open করে check করো।

### Step 3: File stage করো

```bash
git add index.html
```

### Step 4: Commit করো

```bash
git commit -m "fix: update homepage content"
```

### Step 5: Push করো

```bash
git push
```

Done.

---

## 26. VS Code GUI Example

ধরি তুমি homepage design change করেছো।

1. VS Code open
2. `Ctrl + Shift + G`
3. Changed file দেখবে:

```text
styles.css
```

4. ওই file-এর পাশে `+` চাপো
5. Commit message লিখো:

```text
style: polish homepage design
```

6. Commit চাপো
7. Sync Changes চাপো

Done.

---

## 27. Common Problems and Fix

### Problem: remote origin already exists

```text
fatal: remote origin already exists
```

Fix:

```bash
git remote -v
git remote set-url origin https://github.com/username/repo-name.git
```

---

### Problem: nothing to commit

মানে কোনো new change নেই।

```bash
git status
```

---

### Problem: rejected push

আগে pull করো:

```bash
git pull
git push
```

---

### Problem: accidentally added `.env`

Stage থেকে remove:

```bash
git restore --staged .env
```

`.env` commit করার আগেই সাবধান হও।

---

## 28. Final Best Practice

```text
✅ ছোট ছোট commit করো
✅ meaningful commit message দাও
✅ push করার আগে project test করো
✅ .env/database commit করো না
✅ বড় change করার আগে backup branch রাখো
✅ VS Code Source Control দিয়ে file দেখে commit করো
✅ সমস্যা হলে git status দেখে সিদ্ধান্ত নাও
```

---

## 29. Recommended Commit Style

```bash
git add index.html
git commit -m "feat: add homepage hero section"
git push
```

```bash
git add styles.css
git commit -m "style: polish homepage design"
git push
```

```bash
git add script.js
git commit -m "fix: improve navigation menu"
git push
```

```bash
git add README.md
git commit -m "docs: add setup instructions"
git push
```

---

## 30. One-Line Summary

GitHub + VS Code workflow:

```text
Code change → Test → Stage → Commit → Push
```

এই process follow করলে beginner হয়েও professional ভাবে project manage করা যায়।
