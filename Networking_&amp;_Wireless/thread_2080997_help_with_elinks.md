---
title: "help with elinks"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by vikkyhacks on 2012-11-05
When i type ***_elinks [http://www.google.com](http://www.google.com)_*** ***_I get "ORACLE DATABASE 10g EXPRESS EDITION LICENSE AGREEMENT"_*** and a full page of that Oracle stuff which is running on port 8080, No matter what website I try to type it only shows that Oracle stuff, I installed Oracle 10 xe very long ago and if I shutdown oracle with the command > service oracle-xe stop and try to use elinks it gives me an error, > unable to retrive proxy://127.0.0.1:8080/<that website> here is my complete port scan report BEFORE stopping oracle(oracle service autostarts during boot)> meow@VikkyHacks:~/Arena/eclipse/pro/src$ n
23/tcp   open  telnet
53/tcp   open  domain
631/tcp  open  ipp
666/tcp  open  doom
902/tcp  open  iss-realsecure
1521/tcp open  oracle
5432/tcp open  postgresql
8080/tcp open  http-proxy after service oracle-xe stop > 23/tcp   open  telnet
53/tcp   open  domain
631/tcp  open  ipp
666/tcp  open  doom
902/tcp  open  iss-realsecure
5432/tcp open  postgresql

... help me get my elinks back !!!

---

