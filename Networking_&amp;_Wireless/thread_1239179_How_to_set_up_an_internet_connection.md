---
title: "How to set up an internet connection ??"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by [3XTORTION] on 2009-08-13
void

---

### Post by mrky on 2009-08-13
Hi,
and welcome to Ubuntu.

From your description it seems to me taht perhaps, you are having a problem with you ISP and not the connection itself, since you are able to see your router.

---

### Post by [3XTORTION] on 2009-08-13
void.

---

### Post by mrky on 2009-08-13
Ok, thats a bit more info i needed.

Try to copy your ip setings from winxp and arrange them the same way in ubuntu.

also this is a long shot, but try to disable your firewall just to see if you can connect
.

---

### Post by WinterWeaver on 2009-08-13
ubuntu, after default install does not have a firewall enabled. (unless this changed sometime in the last 2 years)

Can you please give more information, on how you are connecting to the internet, your hardware etc. Are you using Dial-up?

---

### Post by [3XTORTION] on 2009-08-13
void.

---

### Post by Iowan on 2009-08-13
I must have missed some background information... 
There is a router, and you can connect to it? **ifconfig -a** will confirm that the card (wired?) has an IP address. If you know the IP address of the router, **route -n** will confirm that it is the default gateway.  BTW, those commands are issued from a terminal.

---

### Post by [3XTORTION] on 2009-08-13
void.

---

### Post by Iowan on 2009-08-13
My DSL uses PPPOE, but the modem handles it all - it's just an ethernet connection to the clients. I had [this]("http://ubuntuforums.org/showthread.php?t=1156441") problem with rfc3442 and DHCP. You can try **sudo dhclient eth0** to see if you get an address - or note the errors.

---

