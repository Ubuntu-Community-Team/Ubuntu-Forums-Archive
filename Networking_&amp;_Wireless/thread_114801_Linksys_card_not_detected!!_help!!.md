---
title: "Linksys card not detected!! help!!"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by beatato on 2006-01-09
I've just installed ubuntu server 5.10 (kernel 2.6.12) after having the same problem with debian.
My computer has 2 network cards:
eth0 for internet connection, embedded, works fine;
eth1 for internal lan: Linksys 10/100/1000 Gigabit Network Adapter
The problem is that I can't configure the second card. When I do lspci, I get this :
0000:01:0a.0 Ethernet controller: Linksys Gigabit Network (rev 10)

I added eth1 to /etc/network/interfaces, then ifup eth1 and I get an error (device not found or something like that)
I installed the tulip module with modconf, but it doesn't do anything.
I don't know what else I can do! Can anyone help me? Thanks

---

### Post by Lambert on 2006-01-09
Have you walked through the wired troubleshoooting thread at the top of this section?

---

### Post by beatato on 2006-01-09
Well, I haven't done lsmod | grep mii, but I guess there's no module associated with that NIC. I don't have the computer here right now, so I can't try that... :(

---

