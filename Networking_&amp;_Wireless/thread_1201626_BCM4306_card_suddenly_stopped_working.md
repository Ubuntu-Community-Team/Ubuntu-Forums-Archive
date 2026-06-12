---
title: "BCM4306 card suddenly stopped working"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by Zettt on 2009-07-01
Hi,


I've installed Ubuntu on my girlfriends laptop. It's a Dell Precision M60. 
It has a Broadcom 4306 card in it. I used [this tutorial]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") to make it work.
Everything was going fine from there on and she had no problem with WLAN connections since then. 

But suddenly it stopped working today.

Any help?

Here is some information for you:

lspci:
```
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

lspci -n | grep 02:03.0
```
02:03.0 0280: 14e4:4320 (rev 02)
```

Some more command outputs can be found in the attachments. 


Thank you.

---

