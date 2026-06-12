---
title: "Wireless network not working on Asus Eee 1005HA with karmic"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Zyndrof on 2009-12-25
Hi,

Recently installed Ubuntu Netbook Remix 9.10 on a new Asus Eee 1005HA and cannot get the wireless network to work...

It is running kernel version 2.6.31-16 and I have installed linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic...

Still cannot get it to work. Any ideas of what I should try next?

Cheers,
Christoffer

---

### Post by bkratz on 2009-12-25
> **Zyndrof said:**
> Hi,

Recently installed Ubuntu Netbook Remix 9.10 on a new Asus Eee 1005HA and cannot get the wireless network to work...

It is running kernel version 2.6.31-16 and I have installed linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic...

Still cannot get it to work. Any ideas of what I should try next?

Cheers,
Christoffer



You really haven't provided much information to go on.  Here is a listing of a lot of threads about you machine in the beginners forum

[http://ubuntuforums.org/search.php?searchid=68481392](http://ubuntuforums.org/search.php?searchid=68481392)

Perhaps something there will help or at least provide you with what information is needed for help.

---

### Post by Zyndrof on 2009-12-25
Sorry, don't really know what information I need to provide.

I found out that the wireless hardware is "RaLink RT3090 Wireless 802.11n 1T/1R PCIe" by running "lspci" in the shell.

---

### Post by bkratz on 2009-12-25
> **Zyndrof said:**
> Sorry, don't really know what information I need to provide.

I found out that the wireless hardware is "RaLink RT3090 Wireless 802.11n 1T/1R PCIe" by running "lspci" in the shell.




There seems to be a lot of information in this thread

[http://ubuntuforums.org/showthread.php?t=1313132&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1313132&highlight=RT3090)

Hopefully something useful. Also here is the actual PPA with drivers as a .deb file

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

Hope something here helps

---

### Post by Zyndrof on 2009-12-25
That did the trick :) Thank you!

---

### Post by bkratz on 2009-12-25
> **Zyndrof said:**
> That did the trick :) Thank you!




Please go to the thread tools at the top of the page and mark the thread as solved.

---

