---
title: "wired networking issues with new zotac machine"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by brydong on 2011-01-03
I can no longer get a new zotac machine I recently built to connect using a wired connection. I'm posting this using my laptop and the same wire I'm trying to get working so I'm reasonably sure the wire is fine.

I had the symptoms described here so I went ahead and installed the listed drivers and blacklisted as described..

[http://ubuntuforums.org/showthread.php?t=1436667&page=5](http://ubuntuforums.org/showthread.php?t=1436667&page=5)

I still, however, cannot get connected.

I'm pasting in the following, hoping it may help troubleshoot:

ifconfig:
eth3      Link encap:Ethernet  HWaddr 00:01:2e:bc:50:4d  
          inet6 addr: fe80::201:2eff:febc:504d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1540 (1.5 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.1 KB)  TX bytes:1120 (1.1 KB)

wlan2     Link encap:Ethernet  HWaddr 74:f0:6d:2a:cc:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lspci:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation GT218 [ION] (rev a2)
03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

---

### Post by PatchesTheCaveman on 2011-01-03
Try running this command and see if it fixes your problem:
```
sudo dhclient eth3
```

If not, copy and paste the output into a reply to this thread and we'll see what we can do.

---

### Post by brydong on 2011-01-04
I did try that and it didn't work. I will post the output hopefully tonight.

---

