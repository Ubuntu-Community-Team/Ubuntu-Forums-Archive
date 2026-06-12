---
title: "Network problem"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by reinaldovp on 2010-04-16
Hi, I've installed Ubuntu 9.10 few days ago, all worked fine
except that I just can load a few internet pages, ([www.google.com](www.google.com),
[www.thepiratebay.org](www.thepiratebay.org)) all the others never load. Neither can load the router configuration page (192.168.1.1 by default)
The OS neither can get updates from Synaptic or apt/get command.
I've read that the problem can be caused by TCP Window Scaling parameter and the solution is disable it in the /etc/sysctl.conf
I did it, but it didn't work.
Other reason possible is IPv6, and is needed disable it in the /etc/sysctl.conf, but this didn't work neither.

My NIC is configured by DHCP, the route is correct (default gw), the resolv.conf (DNS) is ok and the probe is that some pages load very well.

I thought that it was the UFW package but is not installed neither Firestarter.

I ran Wireshark and made captures from visiting [www.google.com](www.google.com)
(load good) and [www.cantv.net](www.cantv.net) (never finish from load) it seems that still change the size of Window TCP.

Is there other place where disable the TCP window scaling?
If someone have any idea?

Thanks...
PD: sorry for my english I'm from Venezuela (speak spanish)

---

### Post by Iowan on 2010-04-16
[Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that discusses MTU - another potential source of trouble. Sometimes, for whatever reason, the interface will be configured with MTU=64 or something similar.

---

### Post by reinaldovp on 2010-04-16
It works...

Thanks a lot

I ran the following command:

sudo ifconfig eth0 mtu 1492

all perfect.

---

### Post by Iowan on 2010-04-16
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by reinaldovp on 2010-04-17
Sorry, it's my first post :)

---

### Post by Iowan on 2010-04-17
> **reinaldovp said:**
> Sorry, it's my first post :)Welcome to Ubuntu and the forums. Don't be sorry - the link was offered as helpful hint, nothing more. :)  I'm pleased you found a solution.

---

