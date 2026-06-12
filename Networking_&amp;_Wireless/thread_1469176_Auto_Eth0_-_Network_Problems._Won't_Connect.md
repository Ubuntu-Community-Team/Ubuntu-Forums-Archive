---
title: "Auto Eth0 - Network Problems. Won't Connect"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by d4x. on 2010-05-02
Upgraded To Ubuntu 10.04 The Other Day. And when I first installed it everything worked great except for my sound card which I fixed. But there was no problem with connecting to my Router via an Ethernet cable. Then I updated the video card drivers, restarted my PC and it wouldn't connect. It would try over around 1-2 mins then tell me its disconnected. No green light activity on the router / network card either.

I've reinstalled fresh copies of Ubuntu a couple of times now, Hoping to get the default settings back. But nothing has worked since.

I looked around the net and found quite a few people had this problem on previous versions of Ubuntu but it would seem most of there fixes were for there Version, so it hasn't helped me.

Heres some info, Let me know if you need more.

ifconfig:
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:29:25:fc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4104 (4.1 KB)
          Interrupt:40 

I've tried all the various things from dhclient to ifup/ifdown etc etc. If someone could help me that would be awesome.

Thank You
-David W

---

### Post by prshah on 2010-05-02
> **d4x. said:**
> No green light activity on the router / network card eithe

The first thing that needs to be checked is if the connection is valid.  Open a terminal (applications-accessories-terminal) and give the command ```
sudo mii-tool eth0
``` please post back the output here for further troubleshooting.

---

### Post by d4x. on 2010-05-02
No, when i use mii-tool it says "eth0: no link"
 
When i use lspci -v it does however show my network card in the list.
 
Any ideas??
 
 
EDIT: Ok i just reset mii-tool and its now saying "eth0: 10mbit, half duplex, link ok"
I still can't connect to the net, but the router has an orange light now, so its detecting each other... but wont connect.

---

### Post by prshah on 2010-05-02
> **d4x. said:**
> No, when i use mii-tool it says "eth0: no link"
 
now saying "eth0: 10mbit, half duplex, link ok"

This is either a very old router, or a very old network card, or something is broken; 10mbit connections, especially half-duplex connections, went out years ago.

If you are sure that 100mbit connections are / should be supported, you can tTry to force full 100mbit full duplex with the command```
sudo mii-tool --force=100baseTx-FD eth0
``` If it shows link OK, then everything should start working fine.

In any case, a 10mbps half duplex connection is no good. I suggest you check the physical cable itself.

---

### Post by Roivai on 2010-05-02
I'm facing similar problems. If I disable autonegotiation using ethtool or mii-tool, I can get a connection, but it is only 10Mbps, half duplex. If I try to force 100Mbps, full duplex like you suggested, the result is:
```
eth0: 100 Mbit, full duplex, no link
```But running:
```
sudo ethtool -s eth0 speed 10 duplex half autoneg off
```makes the connection to work. Very slowly of course.

There is a bug report for ethernet cards using r8169-driver. I guess the starter of this thread uses the same driver?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984)

I think the only thing to do is to wait a fix for that bug, at least with my skills.. :) Or of course I'm happy to hear any suggestions?

---

### Post by prshah on 2010-05-02
> **d4x. said:**
> now saying "eth0: 10mbit, half duplex, link ok"

> **Roivai said:**
> 
```
sudo ethtool -s eth0 speed 10 duplex half autoneg off
```makes the connection to work.

For further information, can both of you please post the outputs for the following terminal commands```
cat /proc/interrupts
lspci|grep -iE network\|ethernet
lsmod | grep -iE e100\|rtl\|mii
```

Can each of you also boot off a live CD (non-lucid) to check the status?

---

### Post by Roivai on 2010-05-02
Here are mine:

```
cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:         55          2          0          0   IO-APIC-edge      timer
  1:          1          0          1          0   IO-APIC-edge      i8042
  3:          0          2          2          3   IO-APIC-edge    
  4:          2          2          2          0   IO-APIC-edge    
  8:          0          1          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          1          1          1          1   IO-APIC-edge      i8042
 16:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb5
 18:          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:       9070       5596     111331      10748   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
 21:    1173492       9709       9745   11918347   IO-APIC-fasteoi   Mantis Core
 22:       6115       1227       1078        603   IO-APIC-fasteoi   HDA Intel
 23:          0          1          0          1   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 28:         43     108668          6          4   PCI-MSI-edge      eth0
 29:      26022       6004      26252        990   PCI-MSI-edge      i915
NMI:          0          0          0          0   Non-maskable interrupts
LOC:     641789     546474     581193     926405   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:      15950      10652      18315      25643   Rescheduling interrupts
CAL:      18941       2419       6234       1854   Function call interrupts
TLB:      28511      23782      30181      21363   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:         30         30         30         30   Machine check polls
ERR:          3
MIS:          0

``````
lspci|grep -iE network\|ethernet
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

``````

lsmod | grep -iE e100\|rtl\|mii
mii                     5237  1 r8169

```And yes, I have tried 9.10 livecd and there the network works normally with 100Mbps switch.

Thanks!

---

### Post by prshah on 2010-05-02
> **Roivai said:**
> 
```
cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
 28:         43     108668          6          4   PCI-MSI-edge      eth0
 29:      26022       6004      26252        990   PCI-MSI-edge      i915

```

Here's a couple of things to check: In your BIOS (Usually, press "F2" or "Del" before GRUB screen apppears), check if you have the following options (or similar thereof) and it's settings:

a) PnP OS / Plug'n'Play OS = Set to enabled
b) PCI Interrupt = If any set to "Level" please change to "Edge".

Please carefully note the changes you make in order to reverse them if the problem does not appear to be affected. Please make only one change at a time, starting the PnP; you should leave PnP to enabled in any case, but if level/edge does not work, put it back the way it was. If the reading is already "Edge" do NOT change to "Level". Do not make any other changes, or, if you have questions, post back with the exact options available and your BIOS details.

I cannot be more specific as to what the options are called or where they exist, since they vary from BIOS to BIOS.

You do these steps at your own risk; there is no real risk here, but my knowledge may be flawed. Sorry about that.

---

### Post by Roivai on 2010-05-02
Unfortunately there seems to be no way to set either of those values in my motherboard's BIOS (Intel D510mo mini-itx board)

---

### Post by Thomas Kenobi on 2010-05-02
Guys, I seem to be having similar problems.

```
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 03
       serial: 90:e6:ba:10:79:56
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:36 ioport:c800(size=256) memory:f6fff000-f6ffffff(prefetchable) memory:f6ff8000-f6ffbfff(prefetchable) memory:fbcf0000-fbcfffff(prefetchable)

```Using          *sudo **ethtool -s eth2 autoneg off* to disable auto-negotiation I'm able to achieve a link, but only half-duplex and at 10Mbps. Trying to force 100Mbps full duplex breaks the connection.

All in all, the problem I'm experiencing conforms to this bug, that was posted earlier: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/564984)

However, the peculiar thing in my case is that I'm also having problems in my Windows installation. I don't know if it is in fact the exact same issue, because I'm unfamiliar with windows diagnostic tools, so I cannot get any details on that end, but the timing is suspiciously close for the issues to be unrelated.


edit:
At the same time, I can connect to the router using a wireless adapter just fine.

```
cat /proc/interrupts
``````

          CPU0       CPU1       CPU2       CPU3
 18:         34          0      78612          0   IO-APIC-fasteoi   ahci, ath
```(I'm assuming this is the wireless adaptor.)

```

          CPU0       CPU1       CPU2       CPU3
 36:        452          0          0          0   PCI-MSI-edge      eth2
```This is the on-board RealTek ethernet.

```
lspci|grep -iE network\|ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
07:03.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

```
ifconfig
eth2      Link encap:Ethernet  HWaddr 90:e6:ba:10:79:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51574 (51.5 KB)  TX bytes:0 (0.0 B)
          Interrupt:36 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125983 (125.9 KB)  TX bytes:125983 (125.9 KB)

wlan0     Link encap:Ethernet  HWaddr [Wireless MAC]  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:cfff:fe10:80c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8927670 (8.9 MB)  TX bytes:1888007 (1.8 MB)

```

---

### Post by wam88 on 2010-10-10
cant really say I had the same exact problem as you, but I had a similar issue where my laptop (Ubuntu 10.04) wouldn't connect using an Ethernet cord, but would connect on wireless.  I fixed my issue by setting IPv6 support to ignore for the auto eth0 settings in the network manager. I don't know nearly enough about Ubuntu to tell you why it would refuse a connection because of IPv6 (does it still not even support IPv6 at all yet??) but that is what worked for me. 

Hope it does something for you too.

---

### Post by crosslink on 2011-04-10
> **wam88 said:**
> I fixed my issue by setting IPv6 support to ignore for the auto eth0 settings in the network manager.
This fixed mine. Thanks!

---

