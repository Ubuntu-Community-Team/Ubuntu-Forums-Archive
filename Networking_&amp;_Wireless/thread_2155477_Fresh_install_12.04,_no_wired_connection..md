---
title: "Fresh install 12.04, no wired connection."
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by sputnik2 on 2013-06-18
I did a fresh install of 12.04, and the ethernet worked great while running it live from a USB. After installation to the HDD, however, I get nothing. No wired or wireless connection. The network manager is just empty. I found a lot of help threads with wired connection issues, but I didn't find one which covered this: 

ifconfig:
```
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1226528 (1.2 MB)  TX bytes:1226528 (1.2 MB)
 
```

There's no mention of eth0 at all. 
I'm new enough to linux that I'm not sure what that means for my system. 

The part of lshw that seemed relevent shows

```
*-network UNCLAIMED                description: Ethernet controller
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:efcfe000-efcfffff
```
and lspci returns

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)



```

/etc/network/interfaces has just two lines about lo, nothing about eth0.

Any ideas why this could be happening?
My wireless and wired are both down, but I'm primarily focused on getting ethernet working first.

---

### Post by praseodym on 2013-06-18
Hi,

load the driver by hand:

```
sudo modprobe -v b44
sudo service network-manager restart
```
Check:```

ifconfig -a
cat /etc/resolv.conf
```

---

### Post by sputnik2 on 2013-06-18
Thanks for the help! The modprobe command never completes, though. It leaves a process running until I Crl-C it.

---

### Post by sputnik2 on 2013-06-18
However, I added b44 to /etc/modules instead and it worked when I rebooted! Thanks so much, it was that module I was missing.

---

