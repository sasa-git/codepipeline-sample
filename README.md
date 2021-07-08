# Note

zshの変数展開で詰んだのでメモ
bashと微妙に違う
```
bash-3.2$ REPO=sasa
bash-3.2$ $REPO
bash: sasa: command not found
bash-3.2$ echo $REPO
sasa
bash-3.2$ IMAGE=$REPO:latest
bash-3.2$ echo $IMAGE
sasa:latest
```

bashで`IMAGE=$REPO:latest`は普通に大丈夫なのに、
zshでは

```
sasa@sasa-MacBook-Pro 0:06:21 [~/Workspace/aws/app-runner-sample] [master]
-> % REPO=sasa
sasa@sasa-MacBook-Pro 0:06:29 [~/Workspace/aws/app-runner-sample] [master]
-> % echo $REPO
sasa
sasa@sasa-MacBook-Pro 0:06:32 [~/Workspace/aws/app-runner-sample] [master]
-> % IMAGE=$REPO:latest
sasa@sasa-MacBook-Pro 0:06:38 [~/Workspace/aws/app-runner-sample] [master]
-> % echo $IMAGE
sasaatest
```

${var}のようにやったら大丈夫だった
```
-> % IMAGE=${REPO}:latest
sasa@sasa-MacBook-Pro 0:02:44 [~/Workspace/aws/app-runner-sample] [master]
-> % echo $IMAGE
sasa:latest
```

bashでもこの書き方で大丈夫
```
bash-3.2$ REPO=sasa
bash-3.2$ echo $REPO
sasa
bash-3.2$ IMAGE=${REPO}:latest
bash-3.2$ echo $IMAGE
sasa:latest
```