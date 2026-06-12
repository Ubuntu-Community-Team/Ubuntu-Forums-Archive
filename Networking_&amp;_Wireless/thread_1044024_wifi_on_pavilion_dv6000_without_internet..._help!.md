---
title: "wifi on pavilion dv6000 without internet... help!"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by joshpilcer on 2009-01-19
Well this sucks. I've been talking to revdog. I'm trying to connect on my HP pavilion dv6000. I've been following this guide: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

but when i get to this part

```
sudo ifconfig wlan0 up
```
i get this error  wlan0: ERROR while getting interface flags: No such device... what do i do? I installed my driver like everything just this part. i have no clue... btw i'm doing this all without internet. i've been sending files back and forth.

---

### Post by mikewhatever on 2009-01-19
Perhaps you really don't have the wlan0 interface. Can you post the output of <ifconfig>. My personal experience also shows that wlan0 is sometimes confused with wlano, but that's just me, hopefully.

---

### Post by superprash2003 on 2009-01-19
also post output of lshw -C network

---

### Post by joshpilcer on 2009-01-19
This is what i got from ifconfig.

```
  
eth0    link encap:Ethernet  HWaddr 00:1b:24:3f:9e:e5
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        Interrupt:18 Base address:0x2000

lo      Link encap:Local loopback
        inet addr:127.0.0.1  Mask:225.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:92 errors:0 dropped:0 overruns:0 frame:0
        TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:4600 (4.4 KB)  TX bytes:4600 (4.4 KB)
```

Here's what i got for lshw -C network

```
WARNING: you should run this program as super-user
   *-network
        description: Network Controller
        product: BCM94311MCG wlan mini-PCI
        vendor: Broadcom Corporation
        physical id: 0
        bus info: pci@0000:03:00.0
        version: 02
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list
        configuration: driver=b43-pci-bridge latency=0 module=ssb

```

---

### Post by mikewhatever on 2009-01-19
Would you also post the output of <lspci -nn | grep 14e4>. What version of Ubuntu do you have? From the howto you linked to and another one [HERE]("http://ubuntuforums.org/showthread.php?t=760568"), it looks like a lot of people still use ndiswrapper. I was under impression that some native linux drivers were developed by broadcom and dell, but apparently not.

---

### Post by joshpilcer on 2009-01-19
For the lspci -nn |grep 14e4 i got:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)
```

I have ubuntu 8.04

---

### Post by mikewhatever on 2009-01-20
> **joshpilcer said:**
> For the lspci -nn |grep 14e4 i got:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)
```

I have ubuntu 8.04

In this case, I think you need to follow the guide and install ndiswrapper. You seem to have followed only the first step.

---

