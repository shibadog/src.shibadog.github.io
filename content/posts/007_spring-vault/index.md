---
title: "spring boot vault"
date: 2020-09-22T14:52:00+09:00
draft: false
toc: false
images:
tags: 
  - spring boot
  - vault
  - sample
---

やってみた。

[Spring Vault](https://spring.pleiades.io/guides/gs/vault-config/)

[Vault](https://www.vaultproject.io/)はHashiCorpのプロダクトで、クレデンシャル情報を保持するミドル。

Vaultはコマンドラインでクレデンシャル情報の設定・取得が可能だが、spring boot vaultを使って、Configurationとしてアプリケーションの設定を連携することができる。

spring cloud configと同様に、 `bootstrap.properties` でVaultへの接続情報を設定することで、読み込みを行うようだ。

`application.yml` を作成してそこからの設定値読み込みと同時に使用しても問題なく使えた。
(まぁ当たり前か。)

RabbitだのAWSだのElasticsearchだののクレデンシャル情報に対応していると記載されているところから、 `bootstrap.properties` で操作することで、対応するミドルウェアのクレデンシャル情報を通常の `application.yml` に設定するのと同様の状態で設定することができるようだ。

---

どのへんでうれしさを感じるのだろうか？  
環境変数で刺すようにするサービスブローカーとどう違うのか。。。？

よりアプリケーションに近い位置でクレデンシャルを設定できるので、良いような悪いような。

コンテナ運用の場合はコンテナ管理ミドルによって環境変数にさしてほしい気もする。

コンテナ管理ミドルを使わずに、手運用デプロイしているときにうれしいとか？  
そんな状況で（クレデンシャル管理が）いる？  
（そんなならば `application.yml` にべた書きしてもよいじゃないか）

K8Sな言葉がちょいちょい出てくるので何か想定する運用があるっぽい気もするけど、調べるの飽きてきたのでそろそろ終わる。
