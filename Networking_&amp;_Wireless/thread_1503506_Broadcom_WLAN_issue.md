---
title: "Broadcom WLAN issue"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by DragonJC on 2010-06-06
I dual boot windows xp and ubuntu 10.04 LTS and the wireless card works perfectly fine in xp so I know its not a hardware/network issue.  In ubuntu, it detects wireless networks, will connect to network and work for about 20 seconds.

> 02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Broadcom Corporation Device 0449
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at e0208000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
and this is what I get when i run a ping on ubuntu

> PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=55 time=26.4 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=55 time=22.7 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=55 time=21.8 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=55 time=22.1 ms
64 bytes from 4.2.2.2: icmp_seq=5 ttl=55 time=21.6 ms
64 bytes from 4.2.2.2: icmp_seq=6 ttl=55 time=22.9 ms
64 bytes from 4.2.2.2: icmp_seq=7 ttl=55 time=22.4 ms
64 bytes from 4.2.2.2: icmp_seq=8 ttl=55 time=21.7 ms
64 bytes from 4.2.2.2: icmp_seq=9 ttl=55 time=23.0 ms
64 bytes from 4.2.2.2: icmp_seq=10 ttl=55 time=23.4 ms
64 bytes from 4.2.2.2: icmp_seq=11 ttl=55 time=22.0 ms
64 bytes from 4.2.2.2: icmp_seq=12 ttl=55 time=21.3 ms
64 bytes from 4.2.2.2: icmp_seq=13 ttl=55 time=30.2 ms
64 bytes from 4.2.2.2: icmp_seq=14 ttl=55 time=22.0 ms
64 bytes from 4.2.2.2: icmp_seq=15 ttl=55 time=30.1 ms
64 bytes from 4.2.2.2: icmp_seq=16 ttl=55 time=23.1 ms
64 bytes from 4.2.2.2: icmp_seq=17 ttl=55 time=22.5 ms
64 bytes from 4.2.2.2: icmp_seq=18 ttl=55 time=23.0 ms
64 bytes from 4.2.2.2: icmp_seq=19 ttl=55 time=23.8 ms
64 bytes from 4.2.2.2: icmp_seq=20 ttl=55 time=23.2 ms
64 bytes from 4.2.2.2: icmp_seq=21 ttl=55 time=25.1 ms
64 bytes from 4.2.2.2: icmp_seq=22 ttl=55 time=22.0 ms
64 bytes from 4.2.2.2: icmp_seq=23 ttl=55 time=22.5 ms
64 bytes from 4.2.2.2: icmp_seq=24 ttl=55 time=23.1 ms
64 bytes from 4.2.2.2: icmp_seq=25 ttl=55 time=37.3 ms
64 bytes from 4.2.2.2: icmp_seq=26 ttl=55 time=23.4 ms
64 bytes from 4.2.2.2: icmp_seq=27 ttl=55 time=27.3 ms
64 bytes from 4.2.2.2: icmp_seq=28 ttl=55 time=24.4 ms
64 bytes from 4.2.2.2: icmp_seq=29 ttl=55 time=21.4 ms
64 bytes from 4.2.2.2: icmp_seq=30 ttl=55 time=25.1 ms
64 bytes from 4.2.2.2: icmp_seq=31 ttl=55 time=230 ms
64 bytes from 4.2.2.2: icmp_seq=32 ttl=55 time=24.5 ms
64 bytes from 4.2.2.2: icmp_seq=33 ttl=55 time=227 ms
64 bytes from 4.2.2.2: icmp_seq=34 ttl=55 time=22.3 ms
64 bytes from 4.2.2.2: icmp_seq=35 ttl=55 time=1401 ms
64 bytes from 4.2.2.2: icmp_seq=37 ttl=55 time=26.2 ms
64 bytes from 4.2.2.2: icmp_seq=38 ttl=55 time=236 ms
64 bytes from 4.2.2.2: icmp_seq=39 ttl=55 time=27.9 ms
64 bytes from 4.2.2.2: icmp_seq=40 ttl=55 time=230 ms


and it continues on after this alternating between a normal 20ms and high ping over 200ms.  The connection refuses to load anything off the internet/local network.

I'm open to any suggestion on fixing this. :(

---

### Post by DragonJC on 2010-06-07
bump

---

### Post by purelinuxuser on 2010-06-07
Hello,

If I'm right (which I hope I am :P), the problem is the b43 driver.  In my experience, it has been buggy and makes annoying, repetitive connection dropouts.  Did I mention speed is stuck at 1 MB/s?  Anyway, your best bet is to try the Broadcom Proprietary STA driver.  To install it, go to System > Administration > Hardware Drivers.  Install the driver by "activating" it.  Reboot, and hopefully wireless will work.

If it doesn't post the output of
```
lshw -c network
```

---

### Post by darkdragn on 2010-06-07
have you tried b43-fwcutter... just worth a try. 
(apt-get install b43-fwcutter)

---

### Post by boonenoob on 2010-06-07
I have had this same problem! to fix it, plug your laptop into an ethernet cable, go to Systerm>Administration>Hardware Drivers and install the stuff it sees for the wireless.
Once you do that, i recommend installing Wicd network manager. it is a great utility for scanning and autoconnecting to networks.

---

### Post by DragonJC on 2010-06-07
You guys are going to love this....

So the issue was the fact I used a WEP key.  I took my laptop to work and connected it to the wireless there that uses WPA and walla, I have a stable connection to the network.  So I took it home and switched my home network to WPA and it works fine now too...

The B43 driver must be having issues with WEP I think.

---

