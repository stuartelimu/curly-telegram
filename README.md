# curly-telegram

## Deploy to Digital Ocean using github

1. login to your server e.g `ssh user@127.0.0.1`

2. create a bare git project in your home directory

```
git init --bare code.git
```

3. create a post-recieve hook in `code.git/hooks/`

```
sudo nano code.git/hooks/post-receive
```

add this to the file

```
#!/bin/sh

# Check out the files
git --work-tree=/home/user/code --git-dir=/home/user/code.git checkout -f
```

here `/home/user/code` is the directory where your files will be deployed

make the file executable

```
chmod +x /path/to/code.git/hooks/post-receive
```

4. create a git repository and clone it to your computer

5. configure your local repository to push to the server

```
git remote set-url origin --add user@127.0.0.1:code.git
```

we are using set-url so that we can push to both our git repository and the server

now run `git push`

### credits
[Git: Push to / Pull from Both Github and Bitbucket](https://blog.kevinlee.io/blog/2013/03/11/git-push-to-pull-from-both-github-and-bitbucket/)

[Deploy a Project to Your Server with Git](https://daveceddia.com/deploy-git-repo-to-server/)

