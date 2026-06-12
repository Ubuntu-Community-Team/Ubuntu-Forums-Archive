---
title: "Wireless works, Ethernet dead"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by intruderukr on 2011-12-07
[INDENT]I've spent a few hours trying to regain my connectivity today.  I have a fresh install of Oneric which had only an ethernet connection.  I made some [changes]("http://ubuntuforums.org/showthread.php?p=11520502#post11520502") to my configuration after which I lost all connectivity.
I found the Broadcom drivers on a thread in the forum which I installed and now I have only wireless working.  Can you please help me restore my wired connection as well?
I'm using Oneric on Dell Inspiron E1405
[/INDENT]Here is some information about my system:
[PHP]**sudo ifconfig -a **
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:79952 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:79952 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6334208 (6.3 MB)  TX bytes:6334208 (6.3 MB) 

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:37:60:70  
          inet6 addr: fe80::216:cfff:fe37:6070/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:329 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3497 (3.4 KB)  TX bytes:77841 (77.8 KB)[/PHP]
[PHP] **lspci** 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01) 
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller 
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) 
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a) 
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05) 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
[/PHP]
[PHP] 
**sudo ifup eth0 **
Ignoring unknown interface eth0=eth0. [/PHP]
 [PHP]**lshw -C Network** 
WARNING: you should run this program as super-user. 
  *-network               
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:efdfc000-efdfffff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=64 
       resources: memory:ef9fe000-ef9fffff 
  *-network 
       description: Wireless interface 
       physical id: 4 
       logical name: wlan0 
       serial: 00:16:cf:37:60:70 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=410.2160 multicast=yes wireless=IEEE 802.11bg 
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. [/PHP]
[PHP]**lspci -nn **
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01) 
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01) 
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01) 
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01) 
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01) 
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01) 
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01) 
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01) 
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01) 
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01) 
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
02:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] 
02:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19) 
02:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a) 
02:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05) 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) [/PHP]
Yes, I'm online and happy with that, but I'd be even happier to have my ethernet back as well. 
Please help! :)
Thanks

---

### Post by praseodym on 2011-12-07
Hi,

tried to load the driver by hand?

```
sudo modprobe -v b44
```

---

### Post by bluexrider on 2011-12-07
NIC driver [http://www.broadcom.com/support/license.php?file=440x/linux-1.00g.zip](http://www.broadcom.com/support/license.php?file=440x/linux-1.00g.zip)

---

### Post by bkratz on 2011-12-07
did you originally use the STA driver for wireless, before b43? If so you may have a blacklisted file in 11.10 located at

/etc/modprobe.d/broadcom-sta-common.conf

If so you will have to see what is in it, there may be a reference to ssb or b44 there.

If so,

try

sudo rm /etc/modprobe.d/broadcom-sta-common.conf

which will simply remove that file ( no damage one way or the other!)

Here is the full description

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by intruderukr on 2011-12-08
Hi,

tried to load the driver by hand?

Code:

sudo modprobe -v b44

Just tried that, works beautifully, thank you very much!

---

### Post by intruderukr on 2011-12-08
> **intruderukr said:**
> Hi,

tried to load the driver by hand?

Code:

sudo modprobe -v b44

Just tried that, works beautifully, thank you very much!
I have to do that each time I log on though...is there is more permanent fix?

---

### Post by intruderukr on 2011-12-08
> **praseodym said:**
> Hi,

tried to load the driver by hand?

```
sudo modprobe -v b44
```
I tried that, seemed to work great at first. But when I logged out and back in I still had no ethernet until I gave the command again.

---

### Post by praseodym on 2011-12-08
Force the driver to load at boot-up:

```
echo b44 | sudo tee -a /etc/modules
```

---

### Post by intruderukr on 2011-12-09
> **bkratz said:**
> did you originally use the STA driver for wireless, before b43? If so you may have a blacklisted file in 11.10 located at

/etc/modprobe.d/broadcom-sta-common.conf

If so you will have to see what is in it, there may be a reference to ssb or b44 there.

If so,

try

sudo rm /etc/modprobe.d/broadcom-sta-common.conf

which will simply remove that file ( no damage one way or the other!)

Here is the full description

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)
Yes, ssb and brr are both blacklisted here, so I'll remove this and see...

---

### Post by intruderukr on 2011-12-09
> **praseodym said:**
> Force the driver to load at boot-up:

```
echo b44 | sudo tee -a /etc/modules
```
Well that looks like it's working.  I'll mark this as solved if it works after several boots.
Thank you!

---

