---
title: "something wrong with pppoe connection"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by nanobahr on 2011-04-29
hello everybody

i know many people had asked much about pppoe connection and its problems ... but i searched for my problem and wasn't lucky to find an answer for it .  my problem is that my eth0 disconnect randomly after setting a pppoe connection to work on startup  >>>>> the pppoe connection working great but when the eth0 auto disconnect it begin to reconnect again and that's ok but i lose the connection for 3 seconds ..

how to stop eth0 from auto disconnect ??

thats with ubuntu 10.10  

Thanks guys >> :popcorn:

---

### Post by dineshs on 2011-04-29
Are you using Network manager DSL tab (GUI) or command pon dsl-provider?

---

### Post by nanobahr on 2011-04-30
Network manager DSL tab (GUI)

and had edited my /etc/rc.local

adding to it these lines to make it run automatic at startup

#----------------for auto connect adsl

killall pppd

ifconfig eth0 up

pon dsl-provider

#----------------

it make it auto connect on startup ok >>> but i think i'm missing something ???

---

### Post by nanobahr on 2011-04-30
guys i found this page and it's realy very helpfull [https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

---

