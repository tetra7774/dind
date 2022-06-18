# DockerSwarm(クラスタリング)

## dind

レポジトリ名：dind  
URL:https://github.com/tetra7774/dind.git

## Overview
docker in docker
→Dockerホストとして動作するコンテナを起動する。今回はdindで起動したコンテナでクラスタリングを行う。

## Requirement
動作確認した環境  
- macOS Catalina 10.15.7
- Docker 20.10.12
## Usage
### composeファイルでコンテナ作成
```docker compose up -d```
### managerコンテナの登録
```docker container exec -it manager docker swarm init```  
    - コマンド実行時にJOINトークンが発行される。このトークンを利用してコンテナをworkerノードとして登録。
### workerコンテナの登録
```docker container exec -it worker01 〜managerコンテナ登録時に標準出力されるコマンド〜```
### ノードの登録状況確認
```docker container exec -it manager docker node ls```  
    - 登録したノード一覧が表示される。  
    - MANAGERbSTATUSに「Leader」にマークがつくコンテナがmanager node


　
## Features
Referenceを参照のこと
## Reference
- [Docker Hub](https://hub.docker.com/_/docker?tab=tags&page=1)
- 実践コンテナ開発入門(p100~p103)







