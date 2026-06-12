---
title: "Cant connect to interent in 10.04 Ubuntu"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by n3xtgen on 2010-05-07
I recently installed a fresh copy of Ubuntu 10.04 on my IBM Thinkpad T43 when I connect to my wireless internet it says that a connection has been astablished but when I run firefox it tells me connection has timed out. Why is this?

**$ lspci**

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)**$ lsusb**
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 3538:0055 Power Quotient International Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**$ iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11g  ESSID:"adamski"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:2C:A7:2A   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=98/100  Signal level=-23 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
**$ ifconfig**
> eth0      Link encap:Ethernet  HWaddr 00:16:41:54:49:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:1c:7e:53  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe1c:7e53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151387 (151.3 KB)  TX bytes:6151 (6.1 KB)
          Interrupt:21 Base address:0xc000 Memory:b4001000-b4001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
Any help please?

Thanks

---

### Post by Iowan on 2010-05-07
What (if anything) can you ping?
router/gateway (by name or IP)?
other LAN machines?
google.com (74.125.95.104)?

---

### Post by n3xtgen on 2010-05-07
I did a ping on youtube and this is what I get:

```
64 bytes from www.youtube.com (74.125.115.102): icmp_seq=1 ttl=52 time=50.2 ms
```

The icmp keeps increments by one and the time keeps changing. Its as if its on a continuous loop and wont stop unless I close the terminal. Is there a setting in **about:config** of firefox that I need to change? What else can I do to make my internet work? It does not even if I plug in through Ethernet:mad:.

Thanks

---

### Post by n3xtgen on 2010-05-08
I went into about:config in firefox and changed the ipv6 to true and now everything i working;). Not sure why this was the reason.

---

### Post by User3k on 2010-05-08
> **n3xtgen said:**
> I did a ping on youtube and this is what I get:

```
64 bytes from www.youtube.com (74.125.115.102): icmp_seq=1 ttl=52 time=50.2 ms
```

The icmp keeps increments by one and the time keeps changing. Its as if its on a continuous loop and wont stop unless I close the terminal. Is there a setting in **about:config** of firefox that I need to change? What else can I do to make my internet work? It does not even if I plug in through Ethernet:mad:.

Thanks

ping -c (number of pings you want goes here) (url or ip address here)

Example:

ping -c 10 google.com

The above example ends after ten pings. Without defining the number with (-c and then the number of pings after) it will ping endlessly.

---

