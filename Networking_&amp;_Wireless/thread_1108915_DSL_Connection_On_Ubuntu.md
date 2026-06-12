---
title: "DSL Connection On Ubuntu"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by mir on 2009-03-28
How I Configure My DSL Connection & Also How I Configure my PC As a Server 
I am installed ubuntu 7.10 and want to make a server

---

### Post by belikralj on 2009-03-28
Try the command

pppoeconf

Then follow the steps to set up your connection
To connect just enter the command:

pon dsl-provider

into terminal and to disconnect

poff

(again in terminal)

Also what kind of server do you want to make?

---

### Post by Naz_Farooq on 2009-03-28
> **belikralj said:**
> Try the command

pppoeconf

Then follow the steps to set up your connection
To connect just enter the command:

pon dsl-provider

into terminal and to disconnect

poff

(again in terminal)

Also what kind of server do you want to make?

Hi, I cannot connect my ubuntu 8.10 to internet and server. My system is connected to the server but I cannot access to it. When I start Windows, it starts browsing and is connected to the server but ubuntu is not connecting to it. Earlier it was browsing but I am facing this problem now a days. I dont know why.

---

### Post by ugm6hr on 2009-03-28
You need to give more detail about your modem and DSL connection.

Also, 7.10 is an old version of Ubuntu.  8.10 is the current, with 9.04 arriving soon.

---

### Post by Naz_Farooq on 2009-03-28
Earlier I used to connect my ubuntu with internet through networ cable but now a days I cannot connect to internet through network cable. In windows internet connection in working but when I start ubuntu. eth0 connection in established but it does not browse or connect me to internet. I cannot access to the server even.
Can anyone help me out of it please.

--
Regards

---

### Post by ugm6hr on 2009-03-28
In Ubuntu:

```
lspci
route -n
```

Post results back here.

---

### Post by Naz_Farooq on 2009-03-30
i did it but it is only showing ip addresses and something i dont understand. Can anyone help me?

---

### Post by coutts99 on 2009-03-30
> **Naz_Farooq said:**
> i did it but it is only showing ip addresses and something i dont understand. Can anyone help me?


Post the results here

---

