---
title: "Wireless troubles, says connected but it isn't"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by h0n0r on 2010-10-30
Hi!


After being a windows *** all my life I've finally taken the decision to start using Linux for real.

So I bought a entire new laptop for the task and it landed on a Acer eMachine 350.


Trouble here trouble there I finally came down to a ubuntu netbook edition, the latest one for the moment.


I had to use jockey-gtk to install drivers to my broadcom network card which took a while, but it now says I have a driver!

Trouble is, when I connect to my WLAN at home it says connected to Gustafsson(Network name) but my interface eth1 looks like this:
```
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:5f:e8:b4  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8aae:1dff:fe5f:e8b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:472616 (472.6 KB)  TX bytes:96420 (96.4 KB)
          Interrupt:45 

eth1      Link encap:Ethernet  HWaddr c4:46:19:45:49:f5  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe45:49f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:18254
          TX packets:14 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3152 (3.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2144 (2.1 KB)  TX bytes:2144 (2.1 KB)
```

As you can see eth0 is a connected wire at the moment. (So I could pastebin the outcomes and post it here.)


So, the router SHOULD give a 192.168.1.* adress, it's a Netgear WGR614v7, but it clearly doesn't.

I tried running sudo iface eth1 192.168.1.90 but no luck there.


lspci gives me the following:
```
lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
```


And the obvious question: Any clues why I get this problem? My wireless security is WPA if that is of any concern.

As I said, I'm a complete beginner at this and what's maybe obvious to you isn't to me :$ (A)


Thanks in advance!

---

### Post by h0n0r on 2010-10-31
Bump

---

### Post by h0n0r on 2010-10-31
All right, I reinstalled the whole OS and now it works! I think I went wrong in the whole update process. :/

---

