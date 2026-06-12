---
title: "Ubuntu 12.04 LTS on dual boot with Win 7, wireless stopped working"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by jaja322 on 2012-05-25
I have been doing some looking around and I can't seem to find an answer to my problem, so I thought i would turn to the Ubuntu community for help.
I have a dual boot system on my Toshiba satellite L755, Windows 7 and Ubuntu 12.04, both 64 bit. until a few weeks ago everything on both OS's was working fine. But now I can't connect to the internet on my Ubuntu side. It can "see" the networks, but it never can connect to them.
I noticed that this happened after Windows 7 updated, and I strongly suspect that this is the culprit. However, I have no clue how to fix it being a complete linux noob. any help is greatly appreciated. thanks in advance.

---

### Post by wildmanne39 on 2012-05-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

