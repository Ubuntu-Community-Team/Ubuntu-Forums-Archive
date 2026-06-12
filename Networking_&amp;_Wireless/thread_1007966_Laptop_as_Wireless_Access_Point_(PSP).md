---
title: "Laptop as Wireless Access Point (PSP)"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by beetlespace on 2008-12-11
OK. Here is the situation. I want to use my laptop as a wireless access point for my PSP. Here's my setup:

Ubuntu 8.10 laptop connects via network cable to Crunchbang PC.
Crunchbang connects to internet via USB 3G wireless broadband connection.

The laptop connects to the internet just fine as does the PC. How do I setup my laptop to use it's internal wireless card as an access point routing all traffic through for my PSP? I did some research and found out my network card on my HP Pavilion DV5 laptop is an Atheros card and checked the drivers. Ubuntu has the proprietary driver installed and everything looks OK there. I have no way to test it though as there are no hotspots anywhere near my home. When I first bought the laptop and installed Ubuntu 8.04 in another city, I did use the wireless and it worked fine.

There is an indicator light that turns from orange to white when the card is on, but so far, just orange.

What config file should I post if any to give any info that might help? What about Network Manager? How should I set this up? I messed around with it a bit, but Network Manager doesn't seem to see my card. I did an iwconfig and got:
lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.

if config gets me this:
eth0 Link encap:Ethernet HWaddr 00:1e:68:cd:f6:0c
inet addr:192.168.0.78 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::21e:68ff:fecd:f60c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:422828 errors:0 dropped:4047560116 overruns:0 frame:0
TX packets:339257 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:549332569 (549.3 MB) TX bytes:34617525 (34.6 MB)
Interrupt:220 Base address:0x6000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1719 errors:0 dropped:0 overruns:0 frame:0
TX packets:1719 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:60628 (60.6 KB) TX bytes:60628 (60.6 KB)

Help?? I already searched Ubuntu forums, and didn't find a solved version of this topic.

---

### Post by superprash2003 on 2008-12-11
post output of lshw -C network from the terminal.. look under sytem->admin->hardware drivers for drivers for your wlan card..

---

### Post by beetlespace on 2008-12-11
```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:cd:f6:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.78 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:93:73:e0:d1:e3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by beetlespace on 2008-12-12
Bump Please.

---

### Post by superprash2003 on 2008-12-12
follow this [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by beetlespace on 2008-12-15
Forget it. I'll just bite the bullet and buy a 3G router when I can afford it. :confused:

---

