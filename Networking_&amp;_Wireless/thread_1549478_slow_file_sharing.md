---
title: "slow file sharing"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by evanct on 2010-08-09
I recently got my D-Link DWA-556 pci card working with my new desktop with Ubuntu 10.04 64-bit. Connection speed is good, but local network file transfer speeds are pitiful. I'm trying to copy some files from my laptop(also running 10.04) and I'm getting around 300-500 kb/s, which is actually lower than my typical download speeds. Anyone know what the problem might be? output of iwconfig is this:

```

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:59:04:0E   
          Bit Rate=0 kb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Googling led me to someone who had been having a similar problem, which was fixed with
```
sudo iwconfig wlan0 rate 54M
```
But that didn't help; in fact it slowed down my transfer rates even further.

---

### Post by Iowan on 2010-08-09
What are you using to copy files (SSH, Samba, etc)? 
You might check MTU (some hints in [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread).

---

### Post by evanct on 2010-08-09
Samba.

I followed that thread, and my ifconfig output is

```
wlan0     Link encap:Ethernet  HWaddr 1c:af:f7:f3:41:94  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1eaf:f7ff:fef3:4194/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84626161 (84.6 MB)  TX bytes:4233591 (4.2 MB)
```

When i ping my router, 1472 is the highest value for MTU that results in a 0% packet loss. However when I ping my ISP, I can't find an MTU value that works - anything above 1472 results in the "Frag needed and DF set (mtu = 1500)" error, while 1472 and everything below it results in a 100% loss.

I also tried going ahead and setting my MTU to 1492, but that didn't help.

---

### Post by evanct on 2010-08-09
Tried using SSH instead of samba, it wasn't any faster.

---

