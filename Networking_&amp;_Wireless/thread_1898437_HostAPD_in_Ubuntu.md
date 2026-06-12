---
title: "HostAPD in Ubuntu"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by hashuntu on 2011-12-21
Hey, I have been trying to set up an access point on my laptop for a couple of weeks with no avail, I am currently trying to use hostapd, and my network does appear on the list of wireless networks however when I try to join it, the client attempting to join just hangs and the laptop AP hangs here,

```
Using interface wlan0 with hwaddr 00:1e:4c:xx:xx:xx and ssid 'testap'
wlan0: STA b8:c7:xx:xx:xx:85 IEEE 802.11: authenticated
wlan0: STA b8:c7:xx:xx:xx:85 IEEE 802.11: associated (aid 1)
wlan0: STA b8:c7:xx:xx:xx:85 RADIUS: starting accounting session 4EF1FDF0-00

```

Here is my ifconfig for wlan0

```
wlan0  Link encap:Ethernet  HWaddr 00:1e:4c:xx:xx:xx 
    inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
    inet6 addr: xxxx::21e:4cff:fe07:bf87/64 Scope:Link
    UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
    RX packets:25361 errors:0 dropped:0 overruns:0 frame:0
    TX packets:16977 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:30312236 (30.3 MB)  TX bytes:2285282 (2.2 MB)

```

and for mon.wlan0

```
mon.wlan0 Link encap:UNSPEC  HWaddr 00-1E-4C-xx-xx-xx-xx-xx-00-00-00-00-00-00-00-00  
    UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
    RX packets:33 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:4521 (4.5 KB)  TX bytes:0 (0.0 B)

```

I followed this tutorial to try and get it running,

[http://blog.dmaggot.org/2010/05/setting-up-an-atheros-based-ap-using-ath5k-and-hostapd/]("http://blog.dmaggot.org/2010/05/setting-up-an-atheros-based-ap-using-ath5k-and-hostapd/")

If anybody could assist me it would be greatly appreciated

---

### Post by hashuntu on 2011-12-21
I found what I think might be a possible answer here however I am not sure what to do as the the solution says it was a kernal problem that was fixed, but I'm running a higher version.. anybody have any idea??

[http://www.linuxquestions.org/questions/linux-networking-3/hostapd-disconnects-wireless-clients-758378/]("http://www.linuxquestions.org/questions/linux-networking-3/hostapd-disconnects-wireless-clients-758378/")

---

### Post by hashuntu on 2011-12-22
Nobody have any idea :( ??

---

### Post by funkypotatoe on 2011-12-23
same problem here, and no luck with seeking a solution (

---

### Post by hashuntu on 2012-01-10
Has anybody got even got their wireless card into **master** mode using ath9k drivers in ubuntu 11.04?

I keep getting the error " Error for wireless request "Set Mode" (8B06) : SET failed on device wlan0 Invalid argument. ; "

Iv'e tried many solutions but none have worked..

---

