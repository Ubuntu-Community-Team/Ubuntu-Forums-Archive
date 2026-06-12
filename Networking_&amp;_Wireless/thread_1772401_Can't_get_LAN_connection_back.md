---
title: "Can't get LAN connection back"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by cheetos316 on 2011-05-31
My machine all of a sudden stopped connecting to the internet.  I use the ethernet port and don't have a wireless connection.  Another computer connects just fine to the router and gets the connection so I know the router and cable modem are working.  I tested the cable and it is working.  I tried plugging the computer directly into the modem but nothing.  

I tried sudo ifconfig eth0 down and then up but nothing.  I tried sudo dhclient eth0 but nothing.  Just keeps saying No DHCPOFFFERS received.  Is there anything else I can try or do?

Thanks!

---

### Post by josephmills on 2011-05-31
what happens when you try ```
sudo ifup eth0 
``` could we see ```
lspci -nn
``` and ```
sudo lshw -C networks 
``` thanks

---

### Post by cheetos316 on 2011-05-31
Here are the results:

> **~:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:5c:e6:eb  
          inet6 addr: fe80::20e:a6ff:fe5c:e6eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2862 (2.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

** ~:~$ sudo ifup eth0**
Ignoring unknown interface eth0=eth0.

** ~:~$ lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM  Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G  Integrated Graphics Controller [8086:2572] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P  Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R)  USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R)  USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R)  USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R)  USB UHCI Controller #4 [8086:24de] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge  [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC  Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R)  IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus  Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER  (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97  Modem Controller [8086:24d6] (rev 02)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100  Ethernet Controller [8086:1050] (rev 02)
01:0e.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 IEEE1394  OHCI 1.1 3-port PHY-Link Ctrlr [1033:00f2] (rev 01)

** ~:~$ sudo lshw -C networks**
PCI (sysfs)
SCSI
Does that make any sense?

Thanks again!

---

### Post by cheetos316 on 2011-06-02
Anyone had an idea of what's going on here?

Thanks!

---

### Post by josephmills on 2011-06-02
```
sudo lshw -C network 
``` and ```
lsmod
```thanks

---

### Post by cheetos316 on 2011-06-02
Interesting turn of events... Got so frustrated with the system that I reset my BIOS and that somehow did the trick.  I am back online!  Although sadly now my USB has decided to drop down to 1.1, but that's a question for another forum.

thanks for the help!

---

### Post by josephmills on 2011-06-02
glad that you got it sorted now to take care of that dang 1.1 to 2.0 have a good one 
Joseph

---

