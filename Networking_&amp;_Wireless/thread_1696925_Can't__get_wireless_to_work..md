---
title: "Can't  get wireless to work."
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by yesz on 2011-02-28
Hello, this is my first post on the forums and I have a problem with my laptop's wireless card. My laptop is  Grundig GNB-250D.
According to lspci my wireless card is a "Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 43)".

I can browse the internet just fine if I use an ethernet cable.
Also the card worked perfectly on Windows Vista.
I tried installing the drivers using Ndiswrapper and it didn't seem to  work (Probably because I did something wrong  :))
By the way I followed this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

---

### Post by chili555 on 2011-02-28
Welcome to the fun, yesz! Let's figure out where we are so far. Please open a terminal and do and post:```
ndiswrapper -l
ls /etc/modprobe.d | grep black
lsmod | grep -e mrv -e ndis
lspci -nn | grep Marv
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

