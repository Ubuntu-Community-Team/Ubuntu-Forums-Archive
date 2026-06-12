---
title: "wireless does not connect on 13.04"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by Bresser on 2013-06-28
Ok so here's my problem. There are similar posts but none have solutions that work for me. I upgraded from Ubuntu 12.04 to 13.04 and on 12.04 and 12.10 my wireless worked fine. But as soon as I boot up into 13.04 it acts like its trying to connect but it never does. Every once in a while it will say disconnected. But then it will try again with again no such luck. I'm on laptop so its got built in wireless card. Its ralink I don't know specific cuz I don't know how to check that. But its 32 bit version I upgraded from a previous version and fresh install is not an option

---

### Post by kc1di on 2013-06-29
go to a terminal and type the following command and list the output here:
```
lspci
```

---

### Post by Bresser on 2013-06-29
Can you tell me what part  need cuz I have to type it by hand

---

### Post by rrich1974 on 2013-06-29
something like "network controller"

---

### Post by kc1di on 2013-06-29
> **Bresser said:**
> Can you tell me what part  need cuz I have to type it by hand

scroll down you should find a line that say wireless controller  or network controller wireless that line will tell 
which ralink card is in your machine.  then we can better address which drivers you may need to install.

---

### Post by steeldriver on 2013-06-29
or you can do

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

which should give you just the relevant entries (including the PCI IDs, which are useful for troubleshooting)

---

### Post by Bresser on 2013-06-29
07:00.0 network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe

---

### Post by kc1di on 2013-06-30
Unfortunately that wireless card is a problem with 13.04 from what I've been able to find.  But here is a thread that may bey of help.

[http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115]("http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115")

Hope it's of some help.  if not I'm afraid for the time being you may have to down grade to 12.04 lts.
Good Luck

---

### Post by Bresser on 2013-06-30
Just one question how do I download a driver if I can't connect to internet

---

### Post by kc1di on 2013-06-30
you have to find a way to get connected via ethernet.

---

### Post by Bresser on 2013-07-10
I have followed the page your gave to me. But after # 5 its just staying like a little blinking white spot. Like what it does when its doing something. But its been liek this for half an hour and nothing has happened.

---

