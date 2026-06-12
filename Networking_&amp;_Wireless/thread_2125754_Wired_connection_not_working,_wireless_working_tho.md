---
title: "Wired connection not working, wireless working though"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by swarupgouru on 2013-03-14
Hi all,

I am new to linux, I installed ubuntu windows installer(wubi) in windows 7.both wireless and wired networks are working in windows.
 
In ubuntu I am unable to connect to wired network. Surprisingly Wireless networks are detected and getting connected. As we plug-in the network cable it doesn't connect automatically? 

I tried re-installing but doesn't works.
 
sudo ifconfig eth0  says

cannot find device "eth0"
eth0: error fetching interface information: Device not found.

Please help me, Thanks in advance :)

---

### Post by varunendra on 2013-03-15
Welcome to the forums swarupgouru :)

Please let us see the output of -
```
lspci -nnk | grep -iA2 net
```

---

### Post by swarupgouru on 2013-03-15
Hi Varunendra, Thanks very much.

i tried the command. following is the output i have got.

swroop@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Lenovo Device [17aa:30a1]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Lenovo Device [17aa:3978]

---

### Post by praseodym on 2013-03-15
Which Ubuntu version do you use? Please show:
```

lsb_release -a
uname -a
```

---

### Post by swarupgouru on 2013-03-16
[FONT=arial][B]Hi Praseodym,

lsb_release -a[/B]
No LSB modules are available.[/FONT]
[FONT=arial]Distributor ID:        Ubuntu[/FONT]
[FONT=arial]Description:        Ubuntu 12.04.2 LTS[/FONT]
[FONT=arial]Release:        12.04[/FONT]
[FONT=arial]Codename:        precise

**uname -a**
[/FONT][FONT=arial]Linux ubuntu 3.5.0-23-generi[/FONT][FONT=arial]c #35~precise1-Ub[/FONT][FONT=arial]untu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][FONT=arial]


[/FONT]

---

### Post by praseodym on 2013-03-16
In this case the backport-modules will not work, because Ubuntu 12.04.2 ships with a later kernel. You need to compile the driver on your own. Instructions here:

[http://forum.ubuntuusers.de/post/4987097/](http://forum.ubuntuusers.de/post/4987097/)

You need to compile again after a kernel upgrade (second black box).

Info: This package does not ship the **lib80211** subsystem drivers which collide with possible Broadcom-STA wireless driver devices.
Therefore, both can be used in parallel if necessary.

---

### Post by swarupgouru on 2013-03-21
Hi, I followed those cmmands, working fine. Thanks a ton.

---

