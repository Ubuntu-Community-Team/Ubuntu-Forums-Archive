---
title: "IPredator, PPTP VPN fails instantly"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by fishbutt2 on 2012-06-05
I have checked the site and many google links.  Checking ipreds tutorial and the one found here [http://ubuntuforums.org/showthread.php?t=1189343](http://ubuntuforums.org/showthread.php?t=1189343).  They did not help

I ran the command to disable UFW, tried directing post 1723 to my computer.  This did not help.  My windows computer on the same network worked perfectly (only required to setup the connection, no change in FW or router).  How can i fix this?

I am running 12.04 64bit basic desktop and have checked that pptp was installed.

My install looks like this [https://ipredator.se/guide/pptp/ubuntu](https://ipredator.se/guide/pptp/ubuntu)

The only other change i have right now is adding 1723 to the iptables  and one person mentioned deleting my default gateway but that just broke my connection.

---

### Post by sammiev on 2012-06-05
You need more than port 1723 open. Please read [post]("http://ubuntuforums.org/showthread.php?t=1876124&highlight=sammiev&page=6") 54. I use a VPN using pptp but my settings are little different than yours.

---

### Post by fishbutt2 on 2012-06-05
> **sammiev said:**
> You need more than port 1723 open. Please read [post]("http://ubuntuforums.org/showthread.php?t=1876124&highlight=sammiev&page=6") 54. I use a VPN using pptp but my settings are little different than yours.
   My UFW is disabled

---

### Post by sammiev on 2012-06-05
All the PPTP I have tried were diffferent from yours. First time I seen one with that setup. Not that it will help but all the ones I tried were like [this]("https://www.witopia.net/support/setting-up-and-using-your-vpn/general-linux-pptp-setup/") and I tried many.

---

