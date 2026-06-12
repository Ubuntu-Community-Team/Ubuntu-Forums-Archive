---
title: "Eth0 missing after Clean 12.04 installation"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by GustavoFerreira on 2012-09-17
Hello,

After a fresh installation of Ubuntu 12.04 on my Asus N56V (dual booting with Win7), one of the most things I noticed, is that eth0 ins't showing.

I have other issues with my Asus, but right now doesn't metter that much (It's the third Asus that I get, and the third one that I always get problems with drivers or anything else,.... what the f*** are they doing different then others?...)

So, bellow is everything I could think of, to put here, so someone can help me with this one.

lshw -C network:
```
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:30:7f:8c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.94 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f783ffff ioport:d000(size=128)
```lspci:
```
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
```

ifconfig -a:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:243616 (243.6 KB)  TX bytes:243616 (243.6 KB)

wlan0     Link encap:Ethernet  HWaddr dc:85:de:30:7f:8c  
          inet addr:192.168.1.94  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de85:deff:fe30:7f8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56234177 (56.2 MB)  TX bytes:3528196 (3.5 MB)

```cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

```Well, you could though that this is a problem of drivers, but just look at this.

lsmod | grep ath:
```
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
```yes, I tried to unload and load the drivers again, no luck at all.

Any ideas?

Thanks in advance!

---

### Post by effenberg0x0 on 2012-09-17
Hey,

No driver has atached to it (not claimed, as we can see in your quote). If I were in this situation I think I'd just try some Atheros module possibilities:

sudo modprobe -r ath9k
sudo modprobe ath9k
lshw -C network: is it still unclaimed? If so, repeat and try again with other module.
sudo modprobe -r ath9k
sudo modprobe ath5k
lshw -C network
etc...

There's info about Atheros bugs, modules and workarounds in Ubuntu wiki and the web. If this relates to using the right module, it shouldn't be hard to solve.

My second guess would be that maybe ath9K is the correct one but is somehow blacklisted in /etc/modprobe.d/*, or not loaded at /etc/modules.

My third guess would relate to Asus more specifically. If this relates to the apparently growing number of discussions regarding problems between recent Asus models hardware particularities and Linux, [like this one]("http://ubuntuforums.org/showthread.php?t=2005756"), some research and tweaking might be needed. 

Regards,
Effenberg

---

### Post by cariboo on 2012-09-17
A bump for the move.

---

### Post by effenberg0x0 on 2012-09-17
Also, have a look at this:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Regards,
Effenberg

---

### Post by GustavoFerreira on 2012-09-17
Thank you very much effenberg0x0.

I did try to remove and add the module again, for 3 times, no luck.

But, as it says in the link you posted, the driver is still in development, and right now, don't want to risk it, using drivers in alpha or beta phase on this pc.

PS: May mark the question as solved, right?

Thanks for your quick answer,

Regards,

Gustavo

---

### Post by Bachi on 2013-04-07
> **GustavoFerreira said:**
> 

But, as it says in the link you posted, the driver is still in development, and right now, don't want to risk it, using drivers in alpha or beta phase on this pc.

I use the by now delivered alx driver, wireless works, but wired ethernet still does not. Haven't had such issues in a long time. I think it is time that we start to rumble on manufacturer's social websites if they still release new hardware without proper linux drivers - this really should be ended now. Place your comments on their social media sites mentioned in the footer of atheros.com .. I certainly did..

---

