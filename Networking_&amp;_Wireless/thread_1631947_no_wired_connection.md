---
title: "no wired connection"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by superbum on 2010-11-27
So I had Ubuntu installed on my computer for several months and I wanted to try mint, so I downloaded and installed.   I of course lost my wireless driver as expected, so I hooked right up to my router, and got nothing.  

So I said no way, i'll just go back to ubuntu, of course my wireless router is gone, but I'm already hooked up to the router so it won't be a big deal.  I have the same problem.  I try turning the wireless off on my netbook (with ubuntu) and connecting, nothing.  I call my isp and they won't help me because I'm using linux. :x

here's what I'm really wondering, is there a way to download the wireless driver I need in full?

I downloaded the package at [http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_4.150.10.5-4_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_4.150.10.5-4_all.deb)
 but I guess that what I got is not the whole thing because when I try to install it it complains I don't have internet access required for additional packages.

---

### Post by MooPi on 2010-11-27
Lets get some info first.From terminal----
```
lspci
less /etc/network/interfaces
ifconfig
```
If you post the results of each of those we can start to trouble shoot your issue

---

### Post by superbum on 2010-11-27
I can't copy and paste but I think this is the important line from lspci

01:0a.0 Network controller: broadcom Corporation BCM4318 [AirForce One 54g] 802.11g wireless LAN controller (rev 02)

less /etc/network/interfaces

auto lo
iface lo inet loopback

ifconfig

eth0   Link encap:Ethernet HWaddr 00:23:54:1f:c9:6f
       inet6 addr: fe80: :223:54ff:felf:c96f/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
       RXvpackets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 b) TX bytes 7066 (7.0 KB)
       Interrupt: 26 Base address:0x2000

lo     Link encap:Local Loopback
       inet addr:127.0.01 mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:72 errors:0 dropped:0 overruns:0 frame:0
       TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
       collision:0 txqueuelen:0
       RX bytes:5600 (5.6 KB) TX bytes:(5600 (5.6 KB)

---

### Post by MooPi on 2010-11-27
You'll need to edit ```
gksudo gedit /etc/network/interfaces
```
Add at the end of the file 
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
```
sudo ifconfig eth0 up
```
Test connection or reboot if that fails.
This is to get your wired connection not wireless.
If that is truly what you want then you'll need a network adapater working to download proper drivers for your Broadcom wireless.

---

### Post by superbum on 2010-11-27
I tried that but it still didn't work.  I really think its my router so I downloaded easytether on my phone and downloaded the driver through my phone.    Now wireless works so I don't really care about the wired connection thanks so much for your time though

---

