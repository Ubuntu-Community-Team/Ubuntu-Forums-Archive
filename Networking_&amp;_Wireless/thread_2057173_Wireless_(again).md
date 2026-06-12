---
title: "Wireless (again)"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by H4Marine on 2012-09-13
Two laptops this one a packard bell with Ubuntu 12.04 and dual boot win7. Win 7 is quick, I've read lots of posts about wireless drivers in Linux not being very good or having problems, is there a fix??

Other laptop tried Linux Mint, that doesn't seem to be able to run the wireless system at all, works ok on ethernet cable.

In Ubuntu wireless internet connection is ssssllllloooooooowwwwwww
Tried switching of power management, looks like this

wlan0     IEEE 802.11bgn  ESSID:"TALKTALK-71BAF4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 34:08:04:71:BA:F4   
          Bit Rate=300 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5175  Invalid misc:609   Missed beacon:0


Thanks 

Off to work for a few hours now I'll check in later.
wireless used to be OK in ubuntu 10.04 but can't find old version?

---

### Post by Bucky Ball on 2012-09-13
[I]Thread moved to [B]Networking & Wireless

[/B][/I]

Please provide the output of:

```
sudo lshw -C networking
```

---

### Post by H4Marine on 2012-09-13
It shows PCI (sysfs) briefly

---

### Post by steeldriver on 2012-09-13
that should be

```
sudo lshw -C **network**
```I think... try that instead

---

### Post by Bucky Ball on 2012-09-13
> **steeldriver said:**
> that should be

```
sudo lshw -C **network**
```I think... try that instead

+1. My mistake, thanks. Post the result of that.

---

### Post by H4Marine on 2012-09-13
Try this...

 ```
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: dc:0e:a1:2d:8c:cc
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
```
  ```
*-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 9c:b7:0d:2a:ab:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic-pae firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0500000-c050ffff
```

---

### Post by H4Marine on 2012-09-13
Back to work now will check in the morning, thanks

---

### Post by Bucky Ball on 2012-09-14
I have edited post #6 for clarity. Please use code tags by clicking 'Go Advanced', marking the code and clicking the hash icon (#). ;)

Well, there are drivers installed for both, the second one the correct one and the first looks like it is part of the kernel you are using. 

For the first machine, it has tg3 driver installed for Broadcom card. Never heard of that driver but that doesn't mean a lot. Hopefully someone that has can chime in. In the meantime, you could try getting online with an ethernet cable, do updates and check 'Additional Drivers'. Anything there with b43 disabled? Check that you have 'b43-fwcutter' and 'firmware-b43-installer' installed, update and try again. 

Broadcom cards work pretty much out of the box now so I am presuming this is a  very recent model card? You might want to have a dig [HERE.]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8OPrlJQ1mwA8kUK5gt.?p=BCM57785%20ubuntu&fr=altavista&fr2=sfp")

---

