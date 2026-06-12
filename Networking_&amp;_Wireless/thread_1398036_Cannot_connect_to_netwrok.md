---
title: "Cannot connect to netwrok"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by bruce01234 on 2010-02-04
Hi,

I just installed ubuntu 9.1 and cant connect to the internet or my local network. I cant even ping anything. I have an XP machine that is working fine on the same router. There is also a DHCP server, but ubuntu doesnt seem to find it to get an IP address.

I read some other posts and turned off ipv6, which didnt make any difference.

Please help

---

### Post by clhsharky on 2010-02-04
HI

How can we help you, we don't know anything of your hardware.
How are you trying to connect, wireless. The stickys are very helpful.

Sharky

---

### Post by bruce01234 on 2010-02-04
Hi,

I am trying to connect by wired network. How do I find out what hardware I have?

Stickys?

---

### Post by clhsharky on 2010-02-04
HI bruce01234


Networking & Wireless
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
 
HOWTO post a Wireless issue (ticket)
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

copy/past in terminel
```
lspci
``` enter

You can copy/past results back. please wrap <>

By the way, Your not the only one with Ethernet problems. Search this site, you might find a solution.


Sharky

Try restarting your router.

---

### Post by Iowan on 2010-02-04
> **bruce01234 said:**
> I am trying to connect by wired network. How do I find out what hardware I have? From a terminal (Applications>Accessories>Terminal) issue the command:```
sudo lshw -C network
``` Post results here (or ask, if you need help getting information transferred).

---

