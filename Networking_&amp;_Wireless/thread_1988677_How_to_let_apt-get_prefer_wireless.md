---
title: "How to let apt-get prefer wireless ?"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by ou_ryperd on 2012-05-28
Hi,

I am using a laptop with 12.04 on. I use VMWare for running a machine that is on my work's domain (via eth0).

I also have a wireless connection (wlan0) with no proxy requirements at work.

I would like to get VMWare to use the eth0 connection, and the host OS itself (12.04) to prefer the wlan0 interface for apt-get, web browsing and so on.

How do I set that up ?

---

### Post by Sergius14 on 2012-05-28
For the Host:

You can try to remove the wired default gateway and only left the wireless one...

Of course that if you have several internal networks, it will no be accessible any more (only the connected LAN):


Or you can try to modify the metrics.... Also Maybe you will have to change from DHCP to Manual.


If you only need this for the VM running on VMWare, you can try to bind that VM to the Wireless Interface and that's shoud be all.

---

### Post by EXXYV on 2012-05-28
I agree with you, thanks for the help in this question. As always all ingenious is simple.

---

