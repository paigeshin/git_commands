# README**s**

**README**s ****are Markdown files, ending with the .md extension.

Markdown is a convenient syntax to generate formatted text. 

It’s easy to pickup!

A README file is used to communicate important information about a repository including:

- What the project does
- How to run the project
- Why it’s noteworthy
- Who maintains the project

---

### [README.md](http://README.md) markdown guide

[https://markdown-it.github.io/](https://markdown-it.github.io/)

---

# .gitignore

- **.DS_Store** will ignore files named .DS_Store
- **folderName/** will ignore an entire directory
- ***.log** will ignore any files with the .log extension
- `#` , comment

---

# Gists

[https://gist.github.com/](https://gist.github.com/)

Github Gists are a simple way to share code snippets and useful fragments with others. Gists are much easier to create, but offer far fewer features than a typical Github repository. 

---

# Github Pages

Githhub Pages is a hosting service for static webpages, so it does not support server-side code like Python, Ruby, or Node. Just HTML/CSS/JS! 

- User Site

⇒ You get one user site per Github account. This is where you could host a portfolio site or some form of personal website. The default url is based on your Github username, following this pattern: **[username.github.io](http://username.github.io)**, though you can change this!

- Project Sites

⇒ You get unlimited project sites! Each Github repo can have a corresponding hosted website. It’s as simple as telling Github which specific branch contains the web content. The default urls follow this pattern: **username.github.io/repo.name**

⇒ branch named `gh-pages` is convention 

---

# Git Command

```bash
# Show logs in one line 
git log --oneline

# Show all logs 
git log 

# Check Username
git config user.name
git config user.email

# Setup your name and email
git config --global user.name "Paige Shin"
git config --global user.email "paigeshin1991@gmail.com"

# Check current git status, 
# sidenotes: do not init a repo inside of a repo
# before running git init, use `git status` to verify that you are not currently inside of a repo
# You can check untracked files 
git status 

# initialize git, create .git directory 
git init 

# delete file from all history
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch ${your_file_to_delete}" HEAD
git push origin +master 

# remove cached file 
git update-ref -d refs/original/refs/heads/master 

# go back to history
git long
git reset --hard ${sha identifier}

# Flow of git
# work on stuff => add changes, commit 

# staging changes - add 
git add ${filename}
# all 
git add .
# individual files
git add demo1.txt demo2.txt demo3.txt 

# commit
git commit -m "${message}"

# Keeping your commits atomic, present tense, imperative
# **keep each commit focused on a single thing.**
git commit -m "change xyz"

# Go to vim 
git commmit 

# vim editor 
# insert
i 
# exit 
:wq

# change default editor
git config --global core.editor "${editor} --wait"
# vscode as default
git config --global core.editor "code --wait" 

# git log in detail
# normal git log 
git log 
# abbreviation
git log --abbrev-commit # commit ae35317 (HEAD -> main)
# pretty printed 
git log --oneline

# amending commits, when you made an error on stating (add) 
# edit staging & commit message 
git add ${file} ${file} ${file}
git commit -m "add headings to all files"
# fix above 
git add ${missing file}
git commit --amend # opens up previous commit message 

# one line, staging & commit
git commit -a -m "${message}"

# When to use branch
# On large projects, we often work in multiple contexts:
# 1. You’re working on 2 different color scheme variations for your website at the same time, unsure of which you like best
# 2. You’re also trying to fix a horrible bug, but it’s proving though to solve. You need to really hunt around and toggle some code on and off to figure it out
# 3. A teammate is also working on adding a new chat widget to present at the next meeting. It’s unclear if your company will end up using it.
# 4. Another coworker is updating the search bar autocomplete.
# 5. Another developer is doing an experimental radical design overhaul of the entire layout to present next month

# Branches
# Branches are an essential part of Git!
# Thinking of branches as alternative timelines for a product.
# They enable us to create separate contexts where we can try new things, or even work on multiple ideas in parallel.
# **If we make changes on one branch, they do not impact the other branches (unless we merge the changes)**

# Master Branch
# Many people designate the master branch as the “source of troth” or the “official branch” for their codebase, but that is left to you to decide.
# From Git’s perspective, the master branch is just like any other branch. It does not have to hold the “master copy” of your project

# HEAD
# We’ll often come across the team **HEAD** in git.
# HEAD is simply a pointer that refers to the current “location” in your repository.
# It points to a particular branch reference.
# So far, HEAD always points to the latest commit you made on the master branch, 
# but soon we'll see that we can move around and HEAD will change

# show all branches 
git branch 

# Creating branch 
git branch ${branch_name}
# Switch branch
git switch ${branch_name} # only changes branch
git checkout ${branch_name} # changes branch and more functionlaities

# Switch vs checkout
# Historically, we used to git `checkout ${branch_name}` to switch branches. This still works.
# The `checkout` command does a million additional things, so the decision was made to add a standalone switch command which is much simpler.
# You will see older tutorials and docs using checkout rather than switch. Both now work.

# switch creating & switching
git switch -c ${branch_name}
 
# deleting branches 
# it's only possible on master 
git switch -d ${branch_name} # The branch must be fully merged in its upstream branch
git switch -d ${branch_name} --force # when not merged 
git siwtch -D ${branch_name} # force delete 

# rename your branch
git switch 1999s
git branch -m 2000s

# Change Master Branch Name 
git branch -M ${name}

# Merging
# Branching makes it super easy to work within self-contained contexts, but often we want to incorporate changes from one branch into another!
# We can do this using the `git merge` command 
# The merge command can sometimes confuse students early on. 
# Remember these two merging concepts:
# - We merge branches, not specific commits
# - We always merge to the current HEAD branch

# Merging Made Easy
# **To merge, follow these basic steps:**
# 1. Switch to or checkout the branch you want to merge the changes into (the receiving branch)
# 2. Use the **git merge** command to merge changes from a specific branch into the current branch 

# To merge the bugfix branch into master
# Master & Bugfix now point to the same commit, until they diverge again 
git switch ${master}
git merge ${branch}

# more information on branches
git branch -v  

# Fast foward Merge (When there are no commits on master) 
git switch ${master}
git merge ${branch}

# Generating Merge Commits (Other branches already had committed on master branches)
# Hopefully there are no conflicts 
git switch ${master}
git merge ${branch} #this prompts `commit message`, commit will be made. 

# Merge Conflicts
# Depending on the specific changes you are trying to merge, Git may not be able to automatically merge. This results in **merge conflicts**, which you need to manually resolve.
# When you encounter a merge conflict, Git warns you in the console that it could not automatically merge.
# It also changes the contents of your files to indicate the conflicts that it wants you to resolve

# Conflict Markers
# The content from your current **HEAD** (the branch you are trying to merge content into) is displayed **between the <<<<<< HEAD and ======**
# The content from the branch you are trying to merge from is displayed **between the ====== and >>>>> symbols**

# Resolving Conflicts
# Whenever you encounter merge conflicts, follow these steps to resolve them.
# 1. Open up the file(s) with merge conflicts
# 2. Edit the file(s) to remove the conflicts. Decide which branch’s content you want to keep in each conflict. Or keep the content from both.
# 3. Remove the conflict “markers” in the document
# 4. Add your changes and then make a commit!
# After resolving the issue
git add ${file}
git commit -m "${message}"

# create branch and go to that branch
git checkout -b ${branch_name}

# Git Diff
# We can use the **git diff** command to view changes between commits, branches, files, our working directory, and more!
# We often use git diff alongside commands like git status and git log, to get a better picture of a repository and how it has changed over time.
# Without additional options, **git diff** lists all the changes in our working directory that are NOT staged for the next commit. 
# Compares Staging Area and Working Directory.
git diff 

# Working Directory Differences (not staged) 
git diff 

# Compare between commits 
git log --oneline
git diff ${old_commit} ${new_commit}
git diff ${old_commit}..${new_commit}

# git add & commit 
git commit -am "${message}"

# lists all changes in the working tree since your last commit
git diff HEAD 

# viewing staged changes 
# git diff --staged or --cached will list the changes
# between the staging area and our last commit
# Show me what will be included in my commit if I run git commit right now 
git diff --staged 
git diff --cached

# Diff-ing Specific Files
# We can view the changes within a specific file by providing git diff with a filename
git diff HEAD ${file_name}
git diff --staged ${file_name}

# Comparing Branches
# git diff branch1..branch2.
# This will list the changes between the tips of branch1 and branch2
git diff ${master}..${branch_name}

# Why we need git stash?
# **Situation**
# - I do some new work, but don’t make any commits
# - What happens when I switch back to master?
# **result**
# 1. My changes come with me to the destination branch(*if branches are not committed)
# 2. Git won’t let me switch if it detects potential conflicts 

# Stashing
# Git provides an easy way of stashing these uncommitted changes so that we can return to them later, without having to make unnecessary commits. 
# Git Stash
# `git stash` or `git stash save` is super useful command that helps you save changes that you are not yet ready to commit. You can stash changes and then come back to them later.
# Running git stash will take all uncommitted changes changes (staged and unstaged) and stash them, reverting the changes in your working copy 
# git stash pop
# Use `git stash pop` to remove the most recently stashed changes in your stash and re-apply them to your working copy

# save uncommited file
git stash # current on ${mybranch} (not master)
git stash save 
git switch ${master} 
git switch ${mybranch}
git stash pop # fetch stashed changes

# You can use `git stash apply` to apply whatever is stashed away, 
# without removing it from the stash.
# This can be useful if you want to apply stashed changes to multiple branches.
git stash # current on ${mybranch}
git switch ${master}
git stash apply # merge conflict can occur
# if merge conflict occurs
git add .
git commit -m "apply stashed changes"
git switch ${mybranch} #`stashed` not applied
git stash apply # on ${mybranch}
git add . git commit -m "apply stashed changes"

# Stashing Multiple Times 
# You can add multiple stashes onto the stack of stashes. 
# They will all be stashed `in the order` you added them. 
git switch ${mybranch1}
git stash 
git switch ${mybranch2}
git stash
git switch ${mybranch3}
git stash

# show stash lists
git stash list # stash@{0}, stash@{1}, stash@{2}

# Applying Specific Stashes
# git assumes you want to apply the most recent stash when you run `git stash aaply`
# but you can also specify a particular stash like `git stash apply stash@{2}` 
git stash apply stash@{2}

# Dropping Stashes
# To delete a particular stash, you can use `git stash drop <stash-id>`
git stash drop stash@{2}

# Checkout
# The **git checkout** command is like a Git Swiss Army knife.
# Many developers think it is overloaded, which is what lead to the addition of the `git switch` and `git restore` commands
# We can use `checkout` to create branches, switch to new branches, restore files, and undo history! 
# We can use `git checkout commit <commit-hash>` to view a previous commit.
# Remember, you can use the `git log` command to view commit hashes. We just need the first 7 digits of a commit hash.
# Don’t panic when you see the following messages 

# git checkout commit to view a previous commit 
git log --oneline
git checkout commit ${7 characters hash code}

# git checkout, time travel, checkout old commits 
git log --oneline
git checkout ${7 characters hash code}

# Detached HEAD??
# You are in ‘detached HEAD’ state. You can look around, make experimental changes and commit them, and you can discard any commits you make in this state without impacting any branches by switching back to a branch

# Detached HEAD
# Don't panic when this happens! It's not a bad thing!
# You have a couple options:
# 1. Stay in detached HEAD to examine the contents of the old commit. Poke around, view the files, etc.
# 2. Leave and go back to wherever you were before - reattach the HEAD
# 3. Create a new branch and switch to it. You can now make and save changes, since HEAD is no longer detached

# Re-attaching our detached HEAD
git checkout ${7 characters hash code}
git switch master 

# Referencing Commits Relative to HEAD
# `git checkout` supports a slightly odd syntax 
# for referencing previous commits relative to a particular commit.
# HEAD~1 refers to the commit before HEAD(parent)
# HEAD~2 refers to 2 commits before HEAD(grandparent)
# This is not essential, but I wanted to mention it 
# because it's quite werid looking if you've never seen it.
# Go to whatever the commit before `head`,
git checkout HEAD~1 # currently detached head

# Discarding changes
# Suppose you've made some changes to a file but don't want to keep them
# To revert the file back to whatever it looked like when you last committed,
# you can use `git checkout HEAD ${file_name} to discard any changes in that file
# reverting back to the HEAD 
# Discard changes
git checkout HEAD ${file_name} 
git checkout HEAD ${file_name} ${file_name2} ${file_name3}

# Another option
# here's another shorter option to revert a file...
# Rather than typing HEAD, you can subsititute 
# -- followed by the file(s) you want to restore 
git checkout HEAD -- ${file_name}
git checkout HEAD -- ${file_name1} ${file_name2}

# Restore
# `git restore` is a brand new Git command that helps with undoing operations
# Becase it is so new, most of the existing Git tutorials and books do not mention it
# But it is worth knowing!
# Recall that `git checkout` does a million different things,
# which many git users find very confusing. 
# `git restore` was introduced alongside `git switch` 
# as alternatives to some of the uses for `checkout`
# Unmodifying Files with Restore
# Suppose you've made some changes to a file since your last commit.
# You've saved the file but then realize you definitely do NOT want those changes anymore!

# To restore the file to the contents in the HEAD, use `git restore ${file_name}`
git restore ${file_name}
# Note above command is not "undoable" if you have uncommited changes in the file
# They will be lost!

# `git restore ${file_name}` restores using HEAD as the default source,
# but we can change that using the `--source` option.
# For example, `git restore --source HEAD~1 home.html`
# will restore the contents of home.html to its state from the commit prior to HEAD.
# You can also use a particular commit hash as the source.
git restore ${file_name}
git log 
git restore --source HEAD~2 ${file_name} # HEAD~2 => Two commits prior to HEAD

# Un-Staging Changes with Git Restore
# If you have accidently added a file to your staging area with `git add` 
# and you don't wish to include it in the next commit, 
# you can use `git restore` to remove it from staging
# Use the `--staged` option like this:
# `git restore --staged app.js`
git restore --staged ${file_name}

# Undoing commits with git rest
# Suppose you've just made a couple of commits on the master branch
# but you actually meant to make them on a separate branch instead.
# To undo those commits, you can use `git reset`
# `git rest ${commit-hash}` will rest the repo back to a specific commit.
# The commits are gone 
git rest ${7_characetrs_commit_hash}

# Reset --hard 
# If you want to undo both the commits 
# AND the actual changes in your files, 
# you can use the `--hard` option.
# for example, `git reset --hard HEAD~1` will delete the last commit
# and associated changes.
# undo commits and change files
git reset --hard ${commit_hash}

# git revert
# Yet another similar sounding and confusing command that has todo with undoing changes.
# `git revert` is simlilar to `git rest` in that they both "undo" changes,
# but they accompish it in different ways.
# `git reset` actually moves the branch pointer backwards, eliminating commits.
# `git revert` instead creates a brand new commit which reverses/undoes the changes
# from a commit. Because it results in a new commit, you will be prompted to enter a commit message
git log --oneline
git revert ${commit_hash}

# Which one should I use?
# Both `git rest` and `git revert` help use reverse changes but there is
# a significant difference when it comes to collaboration
# (which we have yet to discuss but is coming up soon!)
# `if you want to reverse some commits that other people already have on ther machines
# you shoud use revert.`
# If you want to reverse commits that you haven't shared with others, use reset and no one will ever know!
git reset ${commit_hash} #remove commits
git revert ${commit_hash} #create a new commit

# clone repository
git clone ${remote_repo_url}

# cloning non-github repos 
git clone ${remote_repo_url_like_gitlab_bitbucket_any_hosted_repo_url}

# SSH Keys
# register SSH Config 
# You need to be authenticated on Github to do certain operations,
# like pushing up code from your local machine.
# Your terminal will prompt you every single time for your Github email and password, unless..
# You generate and configure an SSH key!
# Once configured, you can connect to Github without having to supply your username/password
[github ssh connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[github ssh connection guide in korea](https://www.lainyzine.com/ko/article/creating-ssh-key-for-github/)

# Remote
# Before we can push anything up to Github, we need to tell Git about our remote repository on Github.
# We need to setup a "destination" to push up to.
# In Git, we refer to these "destinations" as remotes.
# Each remote is simply a URL where a hosted repository lives.

# Check remote repository
git remote -v 

# Adding A New Remote
# A remote is really two things: a URL and a label.
# To add a new remote, we need to provide both to Git.
git remote add ${name} ${url}

# real example
git remote add origin https://github.com/blah.repo.git

# Origin?
# `Origin` is a conventional Git remote name, but it is not at all special.
# It's just a name for a URL
# When we clone a Github repo, the default remote name setup for us is called origin.
# You can change it.
# Most people leave it.

# Rename remote 
git remote rename ${old} ${new}
git remote remove ${name}

# Git Push
git push ${remote} ${branch} 
git push origin master 

# Git Push In Detail
# While we often want to push a local branch up to a remote branch of the same name,
# We don't have to!
# To push our local pancake branch up to a remote branch called waffle we could do:
# `git push origin pancake:waffle`
git push ${remote} ${local_branch}:${destination_remote_branch}
git push origin pancake:waffle 

# The -u option
# The -u option allows us to set the upstream of
# the branch we're pushing
# You can think of this as a link connecting our local branch to a
# branch on Github
# Runnig `git push -u origin master` sets the the upstream of
# the local master branch so that it tracks the master branch
# on the origin repo
# What this means...
# Once we've set the upstream for a branch,
# we can use the `git push` shorthand which will push
# our current branch to the upstream
git push -u origin master  
git push # on `master branch` instead of git push origin master 

# specific case (not used)
git push -u ${remote} ${local_branch}:${remote_branch}
git push -u origin dogs:cats  

# Rename branch
git branch -M main # current branch will be renamed `main`    

# Fetching & Pulling 
# Remote Tracking Branches
# "At the time you last communicated with this remote repository,
# here is where x branch was pointing"
# "They follow this pattern <remote>/<branch>".
#   - `origin/master` references the state of the master branch on the remote repo named origin.
#   - `upstream/logoDesign` references the state of the logoRedesign branch on the remote named upstream(a common remote name)

# take a look at the remote branch
git branch -r 

# You can checkout these remote branch pointers
git checkout origin/master 

# Working with remote branches 
# Once you've cloned a repository, we have all the data
# and Git history for the project at that moment in time.
# However, that does not mean it's all in my workspace!

# The github repo has a branch called `puppies`, but when I
# run `git branch` I don't see it on my machine!
# All I see is the master branch. What's going on? 
# Remote branches
# Run `git remote -r` to view the remote branches our local repository knows about.
# Check remote branches
git branch -r 

# checkout to look around remote branch 
git checkout ${remote_branch} # detached HEAD.
git checkout origin/puppies 

# connect with remote branch locally with `git checkout`
git checkout --track ${remote_branch}
git checkout --track origin/puppies

# connect with remote branch locally
git switch ${remote_branch}
git switch origin/puppies

# Fetching vs Pulling
# The remote repo has changed! 
# A teammate has pushed up changes to the master branch,
# but my local repo doesn't know!
# How do I get those changes?
# Git Fetch, Remote Repository => Local Repository
# Git Pull, Remote Repository => Local Repository => Staging => Workspace 
# Fetching
# Fetching allows us to download changes from a remote repository,
# BUT those changes will not be automatically integrated inout our working files.
# It lets you see what others have been working on,
# `without having to merge those changes` into your local repo.
# Think of it as "please go and get the latest information from Github"
# "But don't screw up my working directory"

# Git Fetch
# The `git fetch ${remote}` command fetches branches and history from a specific remote repository.
# `It only updates remote tracking branches`.
# `git fetch origin` would fetch all changes from the origin remote repository
git fetch ${remote} #if remote is not specified, ${remote} defaults to origin.
git fetch origin
git fetch ${remote} ${branch}
git fetch origin master 
# I now have those changes on my machine
# But if I want to see them, I have to `checkout origin/master`.
# My master branch is untouched!

# demostration
git status
git fetch origin
git checkout origin/movies # visit fetched repo
git switch movies 
git switch food
# new branch added on remote repo
git fetch # fetch new branch
git branch -r # check fetcehd repos 

# Pulling
# `git pull` is another command we can use to retreive
# changes from a remote repository. Unke fetch, pull
# actually updates our HEAD branch with whatever 
# changes are retrieved from the remote. 
# "go and download data from Github AND immediately 
# update my local repo with those changes"
# git pull = git fetch + git merge
# git fetch: update the remote tracking branch with the latest changes from the remote repository
# git merge: update my current branch with whatever changes are on the remote tracking branch

# git pull
# to pull, we specify the particular remote and branch we
# want to pull using `git pull ${remote} ${branch}. Just like
# with git merge, it matteres WHERE we run this command from.
# Whatever branch we run it from is where the changes will be merged into.
# `git pull origin master` would fetch the latest information
# from the origin's master branch and merge those
# changes into our current branch.
git pull ${remote} ${master}

# resolve merge conflicts 
git pull origin food #conflict happens
git add ${any_file}
git commit -m "fix merge conflicts"
git push origin food 

# shorter syntax 
git pull # whatever tracking connection is set, or default branch (origin/master) 

# setting up connection to remote server with `swtich`
git switch origin/food 
git switch origin/master 
git switch origin/puppies
git pull # current branch is puppies, therefore pull puppies from remote repo

# git fetch vs git pull once again
# git fetch
# - Get changes from remote branch(es)
# - Updates the remote-tracking branches with the new changes
# - Does not merge changes onto your current HEAD branch
# - Safe to do at anytime
# git pull
# - Gets changes from remote branch(es)
# - Updates the current branch with the new changes, merging them in
# - Can result in merge conflicts
# - Not recommended if you have uncommitted changed! 

# Workflow, merge branch
git switch ${master}
git pull origin master 
git merge ${branch_name}
git push origin ${master}

# Resolve pull request merge conflict

# From your project repository, bring in the changes and test
git fetch ${remote}
git fetch origin
git checkout -b ${branch} ${remote/branch}
git checkout -b mybranch origin/mybranch # or `git siwtch mybranch`
git merge ${main}
git merge main 

# Resolve Pull Request Merge Conflict( the changes and updates on Github )  
git checkout ${main}
git checkout main  
git pull ${remote} ${main}
git pull origin main 
git merge --no-ff ${mybranch}
git merge --no-ff mybranch 
git push ${remote} ${main}
git push origin main 

# Fork and Pull Request - especailly when working with open source 
git clone ${remote_repository}
git remote -v # Check remote urls 
# add url of original repository
git remote add upstream ${original_remote_repository}
git remote -v # You can check `upstream` added 
# get changes from original remote 
git pull upstream ${branch_name}
git pull upstream main 
# request
git add ${file}
git commit -m "${message}"
git push origin ${main}
# make a pull request on forked repository (from my remote repository to original repository)

# Rebasing
# When I first learned Git, I was told to avoid rebasing at all costs
# It can really #%@* things up
# It's not for beginners! 
# So I avoided the `git rebase` command for YEARS!
# It's actually very useful, as long as you know when
# `NOT` to use it.
# There are two main ways to use the git rebase command:
# - as an alternative to merging
# - as a cleanup tool 

# The ${feature} branch has a bunch of merge commits.
# If the master branch is very active,
# my ${feature} branch's history is muddied.

# Rebasing!
# We can instead rebase the ${feature} branch onto the master branch.
# This moves the entire feature branch so that it BEGINS at 
# the tip of the master branch. All of the work
# is still there, but `we have re-written history`.

# Instead of using a merge commit, rebasing
# rewrites history by `creating new commits` for
# each of the original feature branch commits.
git switch feature
git rebase master # rewriting history, new history, cleans up history
 
# DONT YOU DARE TRY TO REBASE WHEN YOU SHARED YOUR COMMIT WITH OTHERS!
# When not to rebase
# Why Rebase?
# We get a much cleaner project history.
# No unnecessary merge commits!
# We end up with a linear project history. 
# Warning!
# `Never rebase commits that have been shared with others.`
# If you have already pushed commits up to Github...
# DO NOT rebase them unless you are positive 
# no one on the team is using those commits. 
# Seriously
# You do not want to rewrite any git history that other people already have.
# It's a pain to reconcile the alternate histories! 

# Handling Conflicts & Rebasing
git switch features
git rebase master # if conflicts occurred 
git status # rebase in progress
git add ${file_name}
git rebase --continue # always follow the instruction

# Introducing Interactive Rebase
# Rewriting History
# Sometimes we want to rewrite,
# delete, rename, or even reorder
# commits (before sharing them)
# We can do this using `git rebase`!

# Interactuve Rebase
# Running git rebase with the -i option will enter the
# interactive mode, which allows us to edit commits, add
# files, drop commits, etc. Note that we need to specify how
# far back we want to rewrite commits.
# Also, notice that we are not rebasing onth another branch.
# Instead, we are rebasing a series of commits onto the 
# HEAD they currently are based on. 
git rebase -i HEAD~4

# Demonstration of interactive rebase
git switch -c my-feat
git switch -i HEAD~9 # HEAD till the nine (nine commits ago) Go back to commit 
# What NOW?
### JUST CHANGE THE COMMAND, NOT THE CONTENT! ###
# In out text editor, we'll see a list of commits alongside a list
# of commands that we can choose from. Here are a couple
# of the more commonly used commands:
# - pick: use the commit
# - reword: use the commit, but edit the commit message
# - edit: use commit, but stop for amending
# - fixup: use commit contents but meld it into previous commit
					 and discourd the commit message => Combine Commit 
# - drop: remove commit 

# Fixing up & Squashing Commits With Interactive Rebase 
# USE `fixup` 
# example)
# pick 22vd2f add top navbar 
# fixup 23vd2f fix navbar typos
# fixup 24vd2f fix another navbar typos
# 23vd2f, 24vd2f will be merged into `22vd2f`
git log --oneline
git rebase -i HEAD~9

# Dropping Commits with Interactive Rebase
# Delete Changes and Commits Entirely 
# example) 
# drop 923b820 my cat made this commit => This commit will be entirely removed 
# pick a354764 Create README.md 
git log --oneline
git rebase -i HEAD~~2

# Edit The Most Commit Message 
git commit --amend

# GIT TAGS
# THE IDEA BEHIND GIT TAGS
# Tags are pointers that refer to particular points in Git 
# history. We can mark a particular moment in time with a
# tag. Tags are most often used to mark version releases in projects
# Think of tags as branch references that do NOT CHANGE.
# Once a tag is created, it always refets to the same commit.
# It's just a label for a commit. 

# THE TWO TYPES OF GIT TAGS
# There are two types of Git tags we can use: lightweight and annotated tags
# `lightweight tags` are .... lightweight. They are jsut a
# name/label that points to a particular co,it.
# `annotated tags` store extra meta data including the 
# author's name and email, the date, and a tagging message
# (like a commit message)

# SEMANTIC VERSIONGING
# The semantic versioning spec outlines a standardized
# versioning system for software releases. It provides a 
# consistent way for developers to give meanig to their
# software releases (how big of a change is this release??)
# Versions consist of three numbers separated by periods. 
# 2.0.0
# MAJOR.MINOR.PATCH 
# MAJOR version when you make incompatible API changes
# MINOR version when you add functionality in a backwards compatible manner, and
# PATCH version when you make backwards compatible bug fixes. 

# PATCH RELEASE, ex) 1.1
# Patch releases normally do not contain new features of
# significant changes. They typically signify bug fixes and
# other changes that do not impact how the code is used 

# Minor Release
# Minor releases signify that new features or functionality have been added,
# but the project is still backwards compatible.
# No breaking changes. 
# The new functionliaty is optional and should not force users to rewrite
# their own code.

# Major Release
# Major releases signify significant changes that is no longer
# backwards compatible. Features may be removed or changed substantilly.

# Viewing & Searching Tags
# VIEWING TAGS 
# git tag will print a list of all tags in the current repository.
# see all list of tags
git tag 

# VIEWING TAGS 
# We can search for tags that match a particular pattern by
# using `git tag -l` and then passing in a wildcard pattern.
# For example, `git tag -l "*beta*" will print a list of tags that 
# include "beta" in their name. 
git tag -l "v17*" # all tag that starts with `v17*` 
git tag -l "*beta*" # all tag with `beta` included

# checkout with tag name
git checkout 15.3.1 # detached head state 

# git diff using tag
git diff v17.0.0 v17.0.1 

# Creating Lightweight Tags
# To create a lightweight tag, use `git tag ${tagName}`
# By default, Git will create the tag referring to the commit
# that HEAD is referencing 

# ADD TAG 
git status
git add README.md
git commit -m "fix typo in README"
git tag v17.0.2

git log --oneline
git add .
git commit -m "some message"
git tag v17.0.3 

# Creating Annotaged Tags
# Use `git tag -a` to create a new annotated tag. Git will
# then open your default text editor and prompt you for
# additional information.
# Simlar to git commit, we can also use the `-m` option to
# pass a message directly and forgo the opening of the text editor  

# ANNOTATED TAG 
git add .
git commit -m "message"
git tag -a v17.1.0
git show v17.1.0

# TAGGING PREVIOUS COMMITS
# So far we've seen how to tag the commit that HEAD references.
# We can also tag an older commit by providing
# the commit hash: `git tag -a <tagname> <commit-hash>
git log --oneline
git tag a <TAG NAME> <COMMIT HASH> 

# Force Tag 
git tag <TAG NAME> <COMMIT HASH> -f 

# Deleting Tag 
git tag <TAG NAME>
git tag -d <TAG NAME> 

# PUSHING TAGS
# Pushing Tags
# By default, the `git push` command doesn't transfer tags to
# remote servers. If you have a lot of tags that you want to 
# push up at once, you can use the `--tags` options to the `git push` command.
# This will transfer all of your tags to the remote server 
# that are not already there  

# ADD SINGLE VERSION TAG 
git push origin v1.0.0
git push origin <VERSION NAME>

# ADD ALL TAG
git push origin --tags 

# GIT CONFIG
git config user.name
git config --local user.name "blabla"
git config --local user.email "blabla@bla.com"

# CHECK 2 COMMITS AGO 
git diff HEAD~2

# KEY-VALUE STROAGE, GIT 
# Let's Try Hashing
echo 'hello' | git hash-object --stdin
# The `--stdin` option tells git hash-object to use the content from stdin
# rather than a file. In our example, it will hash the world 'hello'

# The echo command simply repeats whatever we tell it to repeat to the
# terminal. We pipe the output of echo to `git hash-object`.

# Rather than simply outputting the key that git would store our object
# under, we can use the `-w` option to tell git to actually write the object to
# the database
# After runnging this command, check out the contents of `.git/objects/`
# we can find results at .git/objects/ 
echo 'hello' | git hash-object --stdin -w 

# Now that we have data stored in our Git object database, we can try
# retrieving it using the git cat-file command.
# The `-p` option tells Git to pretty print the contents of the object bsed on
# its type.
git cat-file -p <object-hash>

# git hash-object 
git hash-object <file.txt>
# store object
git hash-object <file.txt> -w

# input 
git cat-file -p ${object-hash} > ${new content to be added}

# Viewing Trees
# Remember that `git cat-file` prints out git objects. In this example, the 
# `master^{tree}` syntax specifies the tree object that is pointed to by the
# tip of our master branch. 
git cat-file -p master^{tree}

git cat-file -t ${hash}
git cat-file -p ${hash}

# REFLOGS, show all the histories in detail (LOCAL ONLY)
# reflogs
# Git keeps a record of when the tips of branches and other
# references were updated in the repo.
# in .git/HEAD file, git keeps track of `Change` of HEAD, 
# ex) whenever we change branch

# We can view and update these
# reference logs using the `git reflog` command.

# LIMITATIONS OF REFLOGS, - ONLY LOCAL CHANGES RECORDED 
# Git only keeps reflogs on your `local` activity.
# They are not shared with collaborators.
# Reflogs also expire.
# Git celans out old entries after around 90 days,
# though this can be configured. 
git log --oneline 

# GIT REFLOG
# The git reflog command accepts subcommands `show`, `expires`, `delete`, and `exists`.
# Show is the only commonly used variant, and it is the default subcommand.

# `git reflog show` will show the log of a specific reference (it defaults to HEAD)
# For example, to view the logs for the tip of the main branch
# we could run `git reflog show main` 
git reflog show HEAD
git reflog 
git reflog show ${BRANCH}

# Add file with content
echo "hahah" > haha.txt

# Reflog References
# We can access specific git refs is `name@{qualifier}`.
# We can use this syntax to access specific ref pointers and can
# pass them to other commands including checkout, reset, and merge. 
git reflog show HEAD
git reflog show HEAD@{10}

git checkout HEAD@{2}
git diff HEAD@{0} HEAD@{5}
git diff HEAD@{0} HEAD@{2}

# What is the difference between git log and Reflog?
# The biggest difference between Git reflog vs log is that
# the log is a public accounting of the repository's commit history
# while the reflog is a private, workspace-specific accounting of 
# the repo's local commits...
# Use the git log command to view the log and use the git reflog command to view the reflog

# WORK FLOW OF REBASE USING REFLOG
git tag BACKUP #create backup 
git tag -l 
git reflog #find commits 
git log HEAD@{47} # check if log is fine
git reset --hard HEAD@{47}

# TIME-BASED REFLOG
# Every entry in the reference logs has a timestamp
# associated with it. We can filter reflogs entries by
# time/date by using ti,e qualifiers like:
# 1.day.ago
# 3.minutes.ago
# yesterday
# Fri, 12 Feb 2021 14:06:21 - 0800
git reflog master@{one.week.ago}
git checkout bugfix@{2.days.ago}
git diff main@{0} main@{yesterday}

git diff HEAD HEAD@{yesterday}
git diff master master@{yesterday
git reflog show HEAD@{2.days.ago}
git reflog show HEAD@{two.days.ago}
git reflog show HEAD@{one.minute.ago}

# RREFLOGS RESCUE
# We can sometimes use reflog
# entries to access commits that seem lost and are not appearing in git log.
git reflogs 
git reset --hard master@{1}

# Undoing A Rebase w/ Reflog - It's A Miracle!
git rebase -i HEAD~4
git reflog show ${branch}
git reset --hard ${commit-hash}

# Writing Custom Git Aliases
# Global Config Files
# Git lloks for the global config file at either ~/.gitconfig or ~/.config/git/config 
# Any configuration variables that we change in the file will be applied
# across all Git repos.
# We can also alter configuration variables from the command line if preferred.
ls .git 
git config --global user.email 
git config --global user.email "paigeshin1991@gmail.com"
git config --global user.name 
git config --global user.name "paige"
```

---

# Git config file `.git/config`

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = https://github.com/paigeshin/DRDozy_SwiftUI.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
[branch "pay"]
	remote = origin
	merge = refs/heads/master
# Custom 
[color]
	ui = true
[color "branch"]
	local = cyan bold 
  current = yellow bold
[color "diff"]
	old = magenta bold
  new = green bold 

# Adding Aliases
# We can easily set up Git aliases to make our Git experience a bit simpler and faster.
#For example, we could define an alias “git ci” instead of having to type “git commit”
# Or, we could define a custom “git lg” command that prints out a custom formatted commit log.
[alias]
		s = status               # git s => git status
		l = log                  # git l => git l 
		showmebranches = branch  # git showmebranches => git branch
    cm = commit -m           # git cm => git commit -m 
```

---

# Useful git Aliases

- https://github.com/GitAlias/gitalias
- [https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/](https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/)
- [https://gist.github.com/mwhite/6887990](https://gist.github.com/mwhite/6887990)

---

# Git Collaboration Workflows

**Critical**

- The Problems With Working  On A Single Branch
- Feature Branch Workflow
- Pull Requests
- Forking
- Fork-And-Clone workflow

**Important**

- Branch Protection Rules

### The Pitfalls Of A Centralized Workflow

AKA Everyone Works On Master / Main 

AKA The Most Basic Workflow Possible

The simplest collaborative workflow is to have everyone work on the master branch (or main, or any other SINGLE branch).

It’s straightforward and can work for tiny teams, but it has quite a few shortcomings!

### The Problem

While it’s nice and easy to only work on the master branch, this leads to some serious issues on teams!

- Lots of time spent resolving conflicts and merging code, especially as team size scales up.
- No one can work on anything without disturbing the main codebase. How do you try adding something radically different in? How do you experiment?
- The only way to collaborate on a feature together with another teammate is to push incomplete code to master. Other teammates now have broken code...

### Feature Branches

DON’T WORK ON MASTER SILLY GOOSE!

Rather than working directly on master/main, **all new development should be done on separate branches!**

- Treat master/main branch as the official project history
- Multiple teammates can collaborate on a single feature and share code back and forth without polluting the master/main branch
- Master/main branch won’t contain broken code (or at least, it won’t unless someone messes up)

### Merging In Feature Branches

At some point new the work on feature branches will need to be merged in to the master branch!

There are a couple of options for how to do this...

1. Merge at will, without any sort of discussion with teammates. JUST DO IT WHENEVER YOU WANT.
2. Send an email or chat message or something to your team to discuss if the changes should be merged in.
3. **Pull Requests!**

### Pull Requests

Pull Requests are a feature built in to products like Github & Bitbucket. **They are not native to Git itself.** 

They allow developers to alert team-members to new work that needs to be reviewed. They provide a mechanism to approve or reject the work on a given branch. They also help facilitate discussion and feedback on the specified commmits.

“I have this new stuff I want to merge in to the master branch... What do you all think about it?” 

### The Workflow

1. Do some work locally on a feature branch
2. Push up the feature branch to Github
3. Open a pull request using the feature branch just pushed up to Github
4. Wait for the PR to be approved and merged. Start a discussion on the PR. This part depends on the team structure. 

### Branch Protection Rules

- on github page, branch tab
- branch name pattern
    - Require pull request reviews before merging

### Fork & Clone: Another Workflow

The “fork & clone” workflow is different from anything we’ve seen so far. Instead of just one centralized Github repository, every developer has their own Github repository in addition to the “main” repo. Developers make changes and push to their own forks before making pull requests.

It’s very commonly used on large open-source projects where there may be thousands of contributors with only a couple maintainers.

### Forking

Github (and similar tools) allow us to create personal copies of other peoples’ repositories. We cll those copies a “fork” of the original.

When we fork a repo, we’re basically asking Github “Make me my own copy of this repo please”.

As with pull requests, forking is not a Git feature. The ability to fork is implemented by Github. 

### Now what? (copy of the repository)

Now that I’ve forked, I have my very own copy of the repo where I can do whatever I want!

I can clone my fork and make changes, add features, and break things without fear of disturbing the original repository.

If I do want to share my work, I can make a pull request from my fork to the original repo.

---

# SSH Connection

[github ssh connection](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

[github ssh connection guide in korea](https://www.lainyzine.com/ko/article/creating-ssh-key-for-github/)

---

# Git behind scene

[Deep dive into ‘`.git`'](https://www.notion.so/Deep-dive-into-git-4ec24136757f4f84ace9c2503fe5eb42)

---

# Other Docs

[Docs ](https://www.notion.so/Docs-73312ea1bbd44e37a3723ca4fe3d9426)
