---
title: "Afghanistan Ethernet"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by BEARSPIDER on 2011-11-06
Morning I have Ubuntu 11.04 and my Ethernet has stopped working. I normally connect to EDGE CITY which is the provider. I typically connect the Ethernet cable and it connects and then i login and it sends me to my home page. After troubleshooting i now believe it is my computer. So i dont know why my Wired Ethernet has just stopped working.

 I recently ran a program called Bleach Bit and that is the only thing i have done recently that could have affected my system besides maybe an update. Can someone help me with a package or command line (i am new) or a program that will help me figure out the problem. I can connect VIA wireless but the connection is so slow, we are taking about byte speeds so i ca virtually do nothing. I couldn't even post on my computer so i had t go to work to do it. So i cannot provide my system information.
This is the best i can do right now.
[http://www.amazon.com/gp/product/B004GHNQE0/ref=oh_o06_s00_i00_details](http://www.amazon.com/gp/product/B004GHNQE0/ref=oh_o06_s00_i00_details)

---

### Post by lisati on 2011-11-06
I thought you said in another thread that you have a Samsung machine, not a Toshiba. :confused:

It might be easier to run a Live CD to backup your data, and do a fresh install.

---

### Post by BEARSPIDER on 2011-11-06
That was for my phone that i was trying to connect to my computer. I would do a fresh install except it would take forever to reinstall all my additional software due to the poor internet. Plus i like to learn how to fix my system.

---

### Post by BEARSPIDER on 2011-11-06
Computer  64 bits
    capabilities: vsyscall64 vsyscall32
System memory
          size: 3869MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
     
*-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 7c:4f:b5:23:69:2f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-12-generic firmware=N/A ip=10.5.50.57 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:e000(size=256) memory:f7e00000-f7e03fff

---

### Post by BEARSPIDER on 2011-11-06
IFCONFIG:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10168 (10.1 KB)  TX bytes:10168 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:23:69:2f  
          inet addr:10.5.50.57  Bcast:10.5.51.255  Mask:255.255.252.0
          inet6 addr: fe80::7e4f:b5ff:fe23:692f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26500570 (26.5 MB)  TX bytes:3759916 (3.7 MB)

Should there be three of these? Shouldnt i have an ETH0 and a WLAN0?

---

### Post by haqking on 2011-11-06
> **BEARSPIDER said:**
> IFCONFIG:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10168 (10.1 KB)  TX bytes:10168 (10.1 KB)

wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:23:69:2f  
          inet addr:10.5.50.57  Bcast:10.5.51.255  Mask:255.255.252.0
          inet6 addr: fe80::7e4f:b5ff:fe23:692f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26500570 (26.5 MB)  TX bytes:3759916 (3.7 MB)

Should there be three of these? Shouldnt i have an ETH0 and a WLAN0?

doesnt look like eth0 is there

try

ifconfig eth0 up

---

### Post by praseodym on 2011-11-06
Please show:
```
cat /etc/udev/rules.d/70-persistent-net.rules
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
```
If you have any connection install the package ethtool and show additionally:

```
sudo ethtool eth0
```

---

### Post by BEARSPIDER on 2011-11-06
jmosh@BearSpider-AO777:~$ lspci | tail
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
03:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

Ok so i believe my Ethernet is disabled no how do i enable it. I checked the boot setup and i didnt see anything to enable.

I tried this too and Nothing.

jmosh@BearSpider-AO777:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device

---

### Post by praseodym on 2011-11-06
Strange, check

lspci

completely.

---

### Post by BEARSPIDER on 2011-11-07
Sorry praseodym I didnt see your post earlier so i will try that.

---

### Post by BEARSPIDER on 2011-11-07
Well i found an ERROR does atkbd serio0 have anything to do with Ethernet? When i get back home i will post the log.
Basically i had a guy with skills look at it and he couldn't find the eth0 anywhere basically the hardware is unavailable so it is not able to be turned on.

---

### Post by BEARSPIDER on 2011-11-13
Well i am not really sure what happened but i reinstalled the Ubuntu and it was still not showing up then a few days later it just poped up and decided to work so my guess i have a hardware issue when i return from Afghan. i will be sending it back to the Manufacturer.

---

