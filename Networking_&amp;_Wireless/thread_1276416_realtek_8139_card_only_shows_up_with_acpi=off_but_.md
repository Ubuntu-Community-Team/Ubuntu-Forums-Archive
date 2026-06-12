---
title: "realtek 8139 card only shows up with acpi=off but wont connect"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by dracule on 2009-09-27
Hello, I am trying to share my connection between 2 ehternet cards. 

I had to pass the parameter "acip=0ff" to grub for my second card (realtek 8139) to even show up in lspci. 

So taht card shows up as eth1, but firestarter wont start to share my connection because it says that "eth1 is not ready"

So any suggestions on how to fix this?

---

### Post by dracule on 2009-09-27
> Link encap:Ethernet  HWaddr 00:08:a1:54:77:fc  
          inet6 addr: fe80::208:a1ff:fe54:77fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:5 Base address:0x1000 

^^^^
ifconfig eth1
> 
$lsmod | grep 8139
8139too                36608  0 
mii                    14464  1 8139too


> lspci | grep 8139
61:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


> dmesg | grep 8139
[    0.561280] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.561301] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.566348] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.566370] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.567569] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.567591] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.568458] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.568480] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.569672] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.569694] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.570548] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.570570] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.571761] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.571783] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.574855] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.607584] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    0.607606] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    1.183812] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    1.183833] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[    5.228799] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.925624] 8139cp 0000:61:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    6.927636] 8139too Fast Ethernet driver 0.9.28
[    8.621040] eth1: RealTek RTL8139 at 0x1000, 00:08:a1:54:77:fc, IRQ 5
[    8.621043] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   25.246769] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[   25.246791] ACPI Error (uteval-0232): Method execution failed [\_SB_.LNKX._STA] (Node ffff88017f813900), AE_ERROR
[  441.192764] 8139too Fast Ethernet driver 0.9.28
[  441.193968] eth1: RealTek RTL8139 at 0x1000, 00:08:a1:54:77:fc, IRQ 5
[  441.193971] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'

---

### Post by dracule on 2009-09-27
problem solved.

---

### Post by JKyleOKC on 2009-09-27
So how did you solve it? I'm having a possibly similar problem and looking for all possible clues...

---

### Post by dracule on 2009-09-27
> **JKyleOKC said:**
> So how did you solve it? I'm having a possibly similar problem and looking for all possible clues...

the card was a local connection card (between my computer and my laptop) and so i switched it from trying to connect to DHCP to "sharing this connection"

---

