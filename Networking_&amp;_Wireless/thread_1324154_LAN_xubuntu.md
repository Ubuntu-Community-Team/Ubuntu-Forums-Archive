---
title: "LAN xubuntu"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by vze57gc8 on 2009-11-12
I previously had ubuntu on my system. because the resolution was low i installed xubuntu(resolution was normal) but xubuntu wouldnt detect my ethernet connection. the orange light in the back lights up. but the network manager displays wired network as disconnected. i tried resetting the modem and the ethernet work on my ubuntu laptop. 
any idea of whats going on, i hope there is nothing wring with my hardware.

---

### Post by Iowan on 2009-11-12
Check (post, if possible) results of **lshw -C network**. 
**ifconfig -a** will probably show no IP address.

---

### Post by vze57gc8 on 2009-11-12
i figured it was my ignorance. while it always auto connect, i had to click on eth0. thanks very much for the help.

---

