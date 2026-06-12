---
title: "Wired Networking Not Working"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by Stakhanovite on 2012-05-08
Hi,

I am running Ubuntu 64-bit 12.04.  It is a new install as of yesterday and everything was working fine until ... my wired connection suddenly dropped and I am unable to get it back again.  A number of things to note here:

This was previously working as there were no wireless networks in range prior to and after the start of this issue.
Another laptop running Ubuntu 11 connected fine with the same cable/connection.
I have installed vmplayer and I have come across people claiming that this killed their wired connection.  However I have not been able to find an appropriate solution.
I am now using a different network at home and experiencing the same problem.

Wireless is working just dandy.

Some output for you to get started with should you choose to help me out.
ifconfig -a :

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:482 (482.0 B)  TX bytes:482 (482.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.116.1  Bcast:192.168.116.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.100.1  Bcast:172.16.100.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:5d:43:0d:05:ca  
          inet addr:172.16.0.74  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::6a5d:43ff:fe0d:5ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3962967 (3.9 MB)  TX bytes:776273 (776.2 KB)

```

**N.B. I can't find eth0.**

lshw -C network

```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 13
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7300000-f733ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:0d:05:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=18.168.6.1 ip=172.16.0.74 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 memory:f7200000-f7201fff


```

** N.B. the   *-network UNCLAIMED **

Does anybody have any suggestions?

---

### Post by nothingspecial on 2012-05-09
*Thread moved to **Networking & Wireless**.*

---

### Post by Stakhanovite on 2012-05-14
*Shameless Bump*

Any suggestions welcome... :)

---

### Post by roelforg on 2012-05-14
It's missing a driver.
```

sudo lsusb
sudo lspci

```
Post the output of those commands

---

### Post by Stakhanovite on 2012-05-15
Thanks.

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 1770:ff00  
Bus 002 Device 003: ID 5986:030c Acer, Inc 
Bus 003 Device 002: ID 03f0:5611 Hewlett-Packard PhotoSmart C3180
Bus 003 Device 003: ID 05bc:0102 3G Green Green Globe Co., Ltd 
```
```

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1213 (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. Device e091 (rev 13)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
```

---

### Post by MSUdom5 on 2012-05-15
Wild Guess: You just bought an MSI GT70?

I did too, and am having the same issues. Were you able to resolve them? I can't get Ubuntu or Fedora to recognize the ethernet controller.

---

### Post by roelforg on 2012-05-15
The thing that stumps me is that your wired nic has an atheros chipset.
I've never seen those outside of wifi cards.

---

### Post by MSUdom5 on 2012-05-15
It's this card:

[http://www.killergaming.com/solutions/Embedded_Ethernet](http://www.killergaming.com/solutions/Embedded_Ethernet)

---

### Post by Stakhanovite on 2012-05-16
> **MSUdom5 said:**
> Wild Guess: You just bought an MSI GT70?

I did too, and am having the same issues. Were you able to resolve them? I can't get Ubuntu or Fedora to recognize the ethernet controller.

No it's a SkyFire:17.3 and I will post a solution should I get one :(

---

### Post by Stakhanovite on 2012-05-16
> **MSUdom5 said:**
> It's this card:

[http://www.killergaming.com/solutions/Embedded_Ethernet](http://www.killergaming.com/solutions/Embedded_Ethernet)

I think you might be right.  How did you arrive at this conclusion?

---

### Post by MSUdom5 on 2012-05-16
It's identified in the specifications of the MSI GT70.  Your PCI device list is EXACTLY the same as mine, down to every detail, which is why I assumed we had the same machine.

The NVidia drivers aren't even available for the 670M, and Ubuntu has no idea what to do with the ethernet controller. I tried Fedora, and it didn't recognize it either. :(

---

### Post by Stakhanovite on 2012-05-16
I noticed the lack of NVidia drivers too which is a mild irritation especially compared to being dependent on the dodgy public wifi here.

---

### Post by mringer on 2012-05-16
I believe that when   lshw    says that something is UNCLAIMED, it means that you are
lacking a device driver. If you cannot find an UB driver for your card, I suggest that
you try    ndiswrapper   which will (maybe)  let you use a windows driver. Search this
forum for ndiswrapper. 

Good luck, sorry I cannot help any further if this fails.

---

### Post by cyboreal on 2012-05-17
can you post some more diagnostic information when you are having the network problem? Post the output of `lspci`, `ifconfig`, `lsmod`, `sudo rfkill list all`, and the last relevant lines from `dmesg`.

I had a similar problem with an Atheros ethernet NIC. Reloading the ethernet driver fixed all the networking problems for both ethernet and wifi:

$ sudo rmmod atl1c
$ sudo modprobe atl1c

Editing /etc/pm/config.d/unload_modules and adding

SUSPEND_MODULES="$SUSPEND_MODULES atl1c"

fixed the problem with eth0 crashing networking after resume. But we need to know what driver is running your Atheros NIC.

---

### Post by MSUdom5 on 2012-05-17
> **cyboreal said:**
> 

fixed the problem with eth0 crashing networking after resume. But we need to know what driver is running your Atheros NIC.

The problem is that there is no driver for this chipset.

---

