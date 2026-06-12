---
title: "Wireless connection unstable"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by amonterou on 2009-03-06
Hi: 

My wireless connection is really unstable. I am using a T60 and the wireless connects but every 20 minutes the connection is lost. It happens also when I'm using a wired connection. I drive an ubuntu 8.10. 
Anybody had this kind of issue?
The wireless has a LEAP security, but that is working.
I don't know what kind of wireless card I'm using, I would appreciate if you can direct me in how to know this and perhaps check if I have the right drivers installed.

---

### Post by pytheas22 on 2009-03-06
The next time it crashes, please run these commands and post the output:
```

lshw -C Network
lspci -nn
dmesg | tail -40
uname -rm
```

---

### Post by amonterou on 2009-03-06
This is the output of the commands above:

**adrianm@adrianm-laptop:~$ lshw -C Network**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:32:0f:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-1 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:2c:88:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.75.46.94 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:b5:74:b8:ce:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**adrianm@adrianm-laptop:~$ lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]

**adrianm@adrianm-laptop:~$ dmesg | tail -40**

[12541.467388] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:92:1f:08:00 SRC=10.75.46.33 DST=224.0.0.251 LEN=73 TOS=0x00 PREC=0x00 TTL=255 ID=52906 PROTO=UDP SPT=5353 DPT=5353 LEN=53 
[12541.876042] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:92:1f:08:00 SRC=10.75.46.33 DST=224.0.0.251 LEN=73 TOS=0x00 PREC=0x00 TTL=255 ID=52907 PROTO=UDP SPT=5353 DPT=5353 LEN=53 
[12542.081333] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:92:1f:08:00 SRC=10.75.46.33 DST=224.0.0.251 LEN=105 TOS=0x00 PREC=0x00 TTL=255 ID=52912 PROTO=UDP SPT=5353 DPT=5353 LEN=85 
[12549.044107] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:92:1f:08:00 SRC=10.75.46.33 DST=224.0.0.251 LEN=105 TOS=0x00 PREC=0x00 TTL=255 ID=52972 PROTO=UDP SPT=5353 DPT=5353 LEN=85 
[12566.657620] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:81:d1:08:00 SRC=10.75.46.90 DST=224.0.0.251 LEN=108 TOS=0x00 PREC=0x00 TTL=255 ID=30320 PROTO=UDP SPT=5353 DPT=5353 LEN=88 
[12593.576242] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=204.146.24.47 DST=10.75.46.94 LEN=89 TOS=0x00 PREC=0x00 TTL=47 ID=16274 DF PROTO=TCP SPT=443 DPT=57097 WINDOW=62928 RES=0x00 ACK PSH URGP=0 
[12604.955040] FIREWALL: IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:00:1f:3b:45:92:1f:08:00 SRC=10.75.46.33 DST=224.0.0.251 LEN=105 TOS=0x00 PREC=0x00 TTL=255 ID=53432 PROTO=UDP SPT=5353 DPT=5353 LEN=85 
[12624.829322] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=85.26.18.30 DST=10.75.46.94 LEN=324 TOS=0x00 PREC=0x00 TTL=113 ID=22401 DF PROTO=TCP SPT=29250 DPT=49799 WINDOW=59616 RES=0x00 ACK PSH URGP=0 
[12628.436189] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=85.26.18.30 DST=10.75.46.94 LEN=1420 TOS=0x00 PREC=0x00 TTL=113 ID=23250 DF PROTO=TCP SPT=29250 DPT=49799 WINDOW=60984 RES=0x00 ACK URGP=0 
[12628.483127] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=85.26.18.30 DST=10.75.46.94 LEN=144 TOS=0x00 PREC=0x00 TTL=113 ID=23251 DF PROTO=TCP SPT=29250 DPT=49799 WINDOW=60984 RES=0x00 ACK PSH URGP=0 
[12628.634678] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=85.26.18.30 DST=10.75.46.94 LEN=1420 TOS=0x00 PREC=0x00 TTL=113 ID=23309 DF PROTO=TCP SPT=29250 DPT=49799 WINDOW=60984 RES=0x00 ACK URGP=0 
[12628.672949] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=85.26.18.30 DST=10.75.46.94 LEN=144 TOS=0x00 PREC=0x00 TTL=113 ID=23310 DF PROTO=TCP SPT=29250 DPT=49799 WINDOW=60984 RES=0x00 ACK PSH URGP=0 
[12713.572185] FIREWALL: IN=wlan0 OUT= MAC=00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00 SRC=204.146.24.47 DST=10.75.46.94 LEN=89 TOS=0x00 PREC=0x00 TTL=47 ID=16275 DF PROTO=TCP SPT=443 DPT=57097 WINDOW=62928 RES=0x00 ACK PSH URGP=0 
[12811.404539] wlan0: deauthenticated (Reason: 2)
[12811.408703] wlan0: authenticate with AP 00:16:c7:8b:92:e0
[12813.384694] wlan0: authenticate with AP 00:16:c7:8b:94:c0
[12825.271355] wlan0: authenticate with AP 00:16:c7:8b:94:c0
[12825.469040] wlan0: authenticate with AP 00:16:c7:8b:94:c0
[12825.470532] wlan0: authenticated
[12825.470546] wlan0: associate with AP 00:16:c7:8b:94:c0
[12825.472704] wlan0: RX AssocResp from 00:16:c7:8b:94:c0 (capab=0x431 status=0 aid=247)
[12825.472714] wlan0: associated
[12827.114057] FIREWALL: IN=wlan0 OUT= MAC= SRC=10.75.46.94 DST=224.0.0.251 LEN=149 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=129 
[12827.116536] FIREWALL: IN=wlan0 OUT= MAC= SRC=10.75.46.94 DST=224.0.0.251 LEN=357 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=337 
[12827.295660] __ratelimit: 2 callbacks suppressed
[12827.295674] martian source 10.75.46.94 from 89.129.60.62, on dev wlan0
[12827.295679] ll header: 00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00
[12827.372871] FIREWALL: IN=wlan0 OUT= MAC= SRC=10.75.46.94 DST=224.0.0.251 LEN=357 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=337 
[12827.441654] martian source 10.75.46.94 from 99.245.43.156, on dev wlan0
[12827.441662] ll header: 00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00
[12827.461929] martian source 10.75.46.94 from 81.86.160.54, on dev wlan0
[12827.461936] ll header: 00:18:de:2c:88:16:00:14:a8:40:36:bf:08:00
[12827.628931] FIREWALL: IN=wlan0 OUT= MAC= SRC=10.75.46.94 DST=224.0.0.251 LEN=357 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=337 
[12827.678842] martian source 10.75.46.94 from 151.20.81.50, on dev wlan0
[12827.678850] ll header: 00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00
[12827.829403] FIREWALL: IN=wlan0 OUT= MAC= SRC=10.75.46.94 DST=224.0.0.251 LEN=333 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=313 
[12827.846464] martian source 10.75.46.94 from 86.141.220.144, on dev wlan0
[12827.846473] ll header: 00:18:de:2c:88:16:00:14:a8:40:40:ff:08:00
[12827.869470] martian source 10.75.46.94 from 79.184.75.208, on dev wlan0
[12827.869477] ll header: 00:18:de:2c:88:16:00:14:a8:40:36:bf:08:00

**adrianm@adrianm-laptop:~$ uname -rm**

2.6.27-11-generic i686
adrianm@adrianm-laptop:~$

---

### Post by pytheas22 on 2009-03-06
Unfortunately I don't see anything that really explains the problem.  But the bits in dmesg about 'martian source' are interesting.  As I understand it, 'martian' packets are ones that hit your computer from an unknown source far away (like Mars :) ), and which shouldn't have been routed to you.  They're supposed to be harmless, but I'm wondering if they have something to do with the connection crashing.  If there are enough of them, they could presumably cause interference with your router's radio signal, or overwhelm your interface (although there don't appear to be too many of them).  Do you have any idea what exists at IP addresses 10.75.46.94 and 86.141.220.144, and could you try shutting those off (or blocking them in your firewall) to see if it makes a difference?

Beyond that, do you have a strange network setup?  Are there any other devices (wired or wireless) that could be interfering?  It might help to change your router to operate on a different channel.  You might also have better luck using [wicd]("http://wicd.sourceforge.net") instead of Network Manager to manage the wireless connection.

I also see that you have some firewall stuff up.  You're positive that's not part of the problem, right?

---

