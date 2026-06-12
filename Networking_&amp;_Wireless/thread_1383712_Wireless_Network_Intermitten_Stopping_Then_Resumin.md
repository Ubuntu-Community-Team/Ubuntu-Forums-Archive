---
title: "Wireless Network Intermitten Stopping Then Resuming"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by kirbys on 2010-01-17
Ubuntu likes to randomly stop the wirless card from working for about 6-15 seconds at a time every couple of minutes and I have no idea why. Browsing the internet I only see it sometimes but when I play World of Warcraft I notice these issues constantly as it is a live internet connection app. I know its ONLY the wireless card because I disconnect from the wireless and plug in directly to the router and all of a sudden problem solved. But today, for example I'm going to a hotel with the laptop and plugging in directly is now not an option :(  Please anything would be great. This is the only issue I'm really having. 

Heres a bunch of copy/paste stuffs from my terminal.
```
$ lspci
00:0a.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

$ lspci -nn | grep 'Atheros Communications Inc'
00:0a.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)

lsusb
Bus 001 Device 003: ID 07c4:3260 Datafab Systems, Inc. 
Bus 001 Device 002: ID eb1a:2750 eMPIA Technology, Inc. ECS Elitegroup G220 integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04d9:a015 Holtek Semiconductor, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0e:8e:08:3e:f3  
          inet6 addr: fe80::20e:8eff:fe08:3ef3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:999 (999.0 B)  TX bytes:4751 (4.7 KB)

lsmod
Module                  Size  Used by
ath5k                 136680  0 
ath                    10304  1 ath5k
cfg80211              109144  3 ath5k,mac80211,ath
edac_core              48876  1 amd64_edac_mod


sudo lshw -C network
[sudo] password for login: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:4c:b3:37
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1000(size=256) memory:d2215000-d22150ff memory:88000000-8801ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:0e:8e:08:3e:f3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:d2200000-d220ffff

lsb_release -d
Description:    Ubuntu 9.10

uname -mr
2.6.31-17-generic x86_64

```

---

### Post by kirbys on 2010-01-18
Bump for HELP!

---

### Post by kirbys on 2010-01-18
Serious so many views not a single suggestion?

---

### Post by kirbys on 2010-01-18
Bump

---

### Post by kirbys on 2010-01-20
Bump yet again...

---

### Post by kirbys on 2010-01-22
Bump

---

### Post by kirbys on 2010-01-22
Bump

---

### Post by kirbys on 2010-01-23
Bump for 6 days now..

---

### Post by kirbys on 2010-01-23
Bump](*,)

---

### Post by movieman on 2010-01-23
I think everyone has problems with the Atheros chips: mine drops out all the time too, at least when using WPA2... it seems pretty reliable on public wireless networks with no encryption.

Supposedly the newer drivers are better than the one that ships with 9.10.

---

### Post by kirbys on 2010-01-24
> **movieman said:**
> I think everyone has problems with the Atheros chips: mine drops out all the time too, at least when using WPA2... it seems pretty reliable on public wireless networks with no encryption.

Supposedly the newer drivers are better than the one that ships with 9.10.
What new drivers? Where can I find em?

EDIT: 
Also, I've gone on open WAN before also but it did the same thing but only worse.

---

### Post by kirbys on 2010-01-24
Bump

---

### Post by movieman on 2010-01-24
> **kirbys said:**
> What new drivers? Where can I find em?

Well, the newer drivers are part of the newer kernels, which Ubuntu presumably won't get until 10.04. If you search here various people have suggested a backports repository to install newer drivers, but I haven't tried that myself.

---

### Post by Troya.one on 2010-01-25
i ve got such problems with BCM4311 on HP dv6 - it is stop workin randomly and i need to restart it manually using hardware switch to get online again...this is blowin my mind each time&)

---

### Post by kirbys on 2010-01-27
Well I'm just gonna go back to Windows, I'm just having too many problems, and no offense to the coders out there but this is by far the worst OS I've used to date. It does have potential, but potential isn't useful. Thanks to the 2-3 people out of 300 that responded, I do appreciate it.

---

