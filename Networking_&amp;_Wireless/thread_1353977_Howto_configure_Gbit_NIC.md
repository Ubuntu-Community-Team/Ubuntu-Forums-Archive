---
title: "Howto configure Gbit NIC"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Azyx on 2009-12-13
Hey.
I wonder were I can change jumboram and MTU and stuff on a GBit-card.... I also wonder what the best value on computers with XP 2500 processor. I want a configuration that not load the system so much. I use the network to filsharing and vnc. The file-transver going very slow.
My NIC-card is:
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)

And they are on 8.06 and 9.10 Ubuntu and one windosXP.

---

### Post by dmizer on 2009-12-13
Do you get the same file transfer speed results from all protocols (FTP, NFS, SCP, etc)?

---

### Post by Azyx on 2009-12-14
> **dmizer said:**
> Do you get the same file transfer speed results from all protocols (FTP, NFS, SCP, etc)?

sshfs and nfs are approximatly the same, but the load and processor work much. It is from 6-7 MB/s to sometimes 2MB/s. There could be a problem with my TA/RAID-card also, but I remember from windos, that the preformas get much better if I those, jumbo-frame, or what the nme is.

---

### Post by dmizer on 2009-12-14
Some linux g-bit drivers cannot handle jumbo frames. What NIC do you have?

---

### Post by Azyx on 2009-12-15
> **dmizer said:**
> Some linux g-bit drivers cannot handle jumbo frames. What NIC do you have?

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)

---

