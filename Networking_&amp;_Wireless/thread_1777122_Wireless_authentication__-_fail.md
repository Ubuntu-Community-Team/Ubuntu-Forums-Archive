---
title: "Wireless authentication  - fail"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by kriss3d on 2011-06-07
Im having a catch-22 problem with wireless authentication.

Users (and we're talking lots of diffrent users on same computer) logs on through a Windows AD server.
The wireless network is setup with PEAP and all that jazz so basicly in order to get connected to the wifi network here you have to supply your login credencials (naturally each user has his/her own).

The catch-22 here is that you wont be able to log on to the computer itself before your login credencials are verified by the server. And you wont get to even connect to the server before youve supplied the login credencials..

Somhow Windows is able to take your username/password and use that to connect to the wifi network to get the server to verify that you are infact a user and thus letting you use the computer at all..

How is that solved in Linux ?? 
(Ubuntu 9.10 - Aparently you cant assume default domain using more recent versions using LW-open higher than V5)

Any suggestions ?

---

### Post by kriss3d on 2011-06-07
Our network is MSCHAP v2 PEAP (WPA Enterprise)

The main problem here is that all guides ive found assumes one user. But how do i make it use whatever login credencials is provided from users uppon logging in to connect to the wifi ?

---

### Post by kriss3d on 2011-06-08
Bump.. cmon.. I cant be the only one with that problem ?

---

