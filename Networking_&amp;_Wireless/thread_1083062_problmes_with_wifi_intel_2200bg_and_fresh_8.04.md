---
title: "problmes with wifi intel 2200bg and fresh 8.04"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by lennyak on 2009-02-28
Hi,
I have strange problem with fresh instalation of ubuntu 8.04 and my intel 2200bg wifi card.
Before reinstalation I had also ubuntu 8.04 and everything worked fine. After reinstalation (from cd downloaded from internet) wifi works only if a network is open (no authentication and no encription). If I set WEP or WPA/WPA2 encryption I can not connect to wifi.

I have tried many configurations but current configuration of my AP is:

Authentication: Open system
Enctyption: WEP 128bit ASCII

I have 2.6.24-23-generic kernel and I use wicd. Wifi card is detected and there is no errors in dmesg after system start
iwlist scan shows all wifi networks around

I have also tried to use ndiswrapper according to this post: [http://ubuntuforums.org/showthread.php?t=896905](http://ubuntuforums.org/showthread.php?t=896905)
wicd shows wifi networks but can not connects to my network to.

Do you have any ideas what can be wrong??
Thanks in advance for any help

---

### Post by chili555 on 2009-02-28
Are you sure your WEP key is ASCII? It's not impossible, It's just rarer than HEX. You can tell by the number of characters:

# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters

---

### Post by lennyak on 2009-02-28
Yes, I'm sure that it is 128bit ASCII

I have found solution for my problem. It was package linux-backports-modules-2.6.24-23-generic. I have removed this package by:

sudo apt-get remove linux-backports-modules-2.6.24-23-generic

and now everything seems to be ok.

---

