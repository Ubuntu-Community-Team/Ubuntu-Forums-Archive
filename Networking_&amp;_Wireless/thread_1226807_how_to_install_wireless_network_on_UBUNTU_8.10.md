---
title: "how to install wireless network on UBUNTU 8.10"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by thuynn on 2009-07-29
hello everybody, I am a newbie. I have installed ubuntu 8.10 on my laptop already. But from now, I cannot access to the internet through wireless even I have install the driver for wireless in Window ( wireless network can be used normally in window).

Have I forgot something else to use wireless network on Ubuntu 8.10? 
Please help me.Thank you in advance :D

---

### Post by mynameinc on 2009-07-29
> **thuynn said:**
> hello everybody, I am a newbie. I have installed ubuntu 8.10 on my laptop already. But from now, I cannot access to the internet through wireless even I have install the driver for wireless in Window ( wireless network can be used normally in window).

Have I forgot something else to use wireless network on Ubuntu 8.10? 
Please help me.Thank you in advance :D

Laptop manufacturer, model and hardware specs (esp. wireless card), please.

---

### Post by superprash2003 on 2009-07-30
post output of **lshw -C network**

---

### Post by thuynn on 2009-08-01
Hi, thank you for reply me.
My laptop is Asus K40IJ Series and some information about it is:
Intel Core 2 DuoT6400 (2x2.0Ghz, 800MHz FSB, 2MB L2 Cache)45nm /14.0" HD (1366x768) LED backlight Splendid /2GB DDR2/ 8001 x SO-DIMM socket up to 4GB /160GB5400 rpmSATAIntel® GMA 4500MHD /8X Super Multi DVDRW Double Layer /802.11 b/g/n6 Cell(2.3kg)/ Linux/China /Pin ~6hrs (SHE Technology) , Ice cool , Keyboard Chocolate , Loa AltecLancing hi&#7879;u &#7913;ng SRS ,1.3MP Camera , Card reader

I have install WinXP and can access the wireless network normally. Then, I installed an other OS: Ubuntu, but in Ubuntu, I do not know how to access the Wireless network.

I have tried the command "lshw -C network" in the Terminal and the output is as the file I attached here.

---

### Post by howefield on 2009-08-01
Try again, there is no file attached ?

---

### Post by thuynn on 2009-08-01
Here is the output in Terminal when I tried the command "lshw -C network":

thuynnbk@thuynnbk-laptop:~$ sudo lshw -C network
[sudo] password for thuynnbk: 
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:fd:3c:72
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.33 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:ea:b4:9c:8f:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

