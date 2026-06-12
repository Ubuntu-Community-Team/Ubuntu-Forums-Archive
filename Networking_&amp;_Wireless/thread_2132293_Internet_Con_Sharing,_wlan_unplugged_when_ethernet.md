---
title: "Internet Con Sharing, wlan unplugged when ethernet connected"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by metalcorpe on 2013-04-04
I own an HP ProBook 4510s Energy Star. I am connected over WiFi to the internet with a broad-com BCM4312 using the b43 driver. I am trying to share my Internet connection to a tp-link access point/client in order to connect more devices to the internet. The problem is that every time i connect the Ethernet cable to my laptop, WiFi, turns off and i cant use it while the Ethernet cable is connected. My biggest problem is that i cant use WiFi and Ethernet at the same time.
Here is my network hardware and configuration
1st when Ethernet unplugged:
Network:
Card-1: Broadcom BCM4312 802.11b/g LP-PHY driver: b43-pci-bridge
Card-2: Marvell 88E8072 PCI-E Gigabit Ethernet Controller driver: sky2
eth0 Link encap:Ethernet HWaddr 18:a9:05:cd:ee:79 UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:1308 errors:0 dropped:0 overruns:0 frame:0 TX packets:1378 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:338312 (338.3 KB) TX bytes:144517 (144.5 KB) Interrupt:17
lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:1257 errors:0 dropped:0 overruns:0 frame:0 TX packets:1257 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:38807 (38.8 KB) TX bytes:38807 (38.8 KB)
wlan0 Link encap:Ethernet HWaddr 90:4c:e5:4d:20:96 inet addr:192.168.1.16 Bcast:192.168.1.255 Mask:255.255.255.0 inet6 addr: fe80::924c:e5ff:fe4d:2096/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:407060 errors:0 dropped:7 overruns:0 frame:0 TX packets:355911 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:451806029 (451.8 MB) TX bytes:42627691 (42.6 MB)
2nd when Ethernet plugged:
Network:
Card-1: Broadcom BCM4312 802.11b/g LP-PHY driver: b43-pci-bridge
Card-2: Marvell 88E8072 PCI-E Gigabit Ethernet Controller driver: sky2
eth0 Link encap:Ethernet HWaddr 18:a9:05:cd:ee:79 inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0 inet6 addr: fe80::1aa9:5ff:fecd:ee79/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:1423 errors:0 dropped:0 overruns:0 frame:0 TX packets:1713 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:346272 (346.2 KB) TX bytes:206229 (206.2 KB) Interrupt:17
lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:1905 errors:0 dropped:0 overruns:0 frame:0 TX packets:1905 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:59829 (59.8 KB) TX bytes:59829 (59.8 KB)
Please inform me if anything else is needed and i will post it as soon as possible. Thank You and sorry for my English. Peace

---

### Post by vandorjw on 2013-04-04
[ATTACH=CONFIG]240946[/ATTACH]

I attached a diagram of what I understand your setup to be. Is this drawing correct? and if it is..., why not run a wire from the Source, to the TP-Link? (Dotted line in gray, which i assume is not there.)

---

### Post by metalcorpe on 2013-04-04
First of all, thanks for your reply
I've been searching for days for a solution and no one replied

yes your diagram is correct
I can't run a wire because of the place the source

The (wlan-Ethernet) bridge works perfect on my previous win7 installation but some time now i have this problem mentiond above, so i guess is a software problem

---

### Post by Iowan on 2013-04-04
The interfaces need to be in different subnets to work concurrently.

---

### Post by metalcorpe on 2013-04-05
I tried different subnet configurations but the problem insists
Even in dhcp or shared ip configuration
I cant even access the wlan module when ethernet is pluged in

---

### Post by lvlint67 on 2013-04-05
This sounds like it MIGHT be a bios thing.... Have you looked through your bios for a relevant option?

---

### Post by metalcorpe on 2013-04-05
Yes
I searched my bios a couple of times
I think that if there was a bios issue thre would be a windows malfuction also when i connect the 2 adapters at the same time..

---

### Post by lvlint67 on 2013-04-05
rfkill unblock wifi
Does that command do anything? Possibly via sudo?

---

### Post by metalcorpe on 2013-04-05
Think i tried this command a few days ago
Let me try it again when i get back home

---

