---
title: "Broadcom and PAE kernel"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by pinballwizard on 2011-03-14
Hi, with reference to this thread: [http://ubuntuforums.org/showthread.php?t=1390979&page=34](http://ubuntuforums.org/showthread.php?t=1390979&page=34)  I have a Lenovo G550, the bit we need from lshw is:  *```
-network                 description: Wireless interface                 product: BCM4312 802.11b/g                 vendor: Broadcom Corporation                 physical id: 0                 bus info: pci@0000:04:00.0                 logical name: eth1                 version: 01                 serial: ac:81:12:05:c8:7e                 width: 64 bits                 clock: 33MHz                 capabilities: bus_master cap_list ethernet physical wireless                 configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.6 latency=0 multicast=yes wireless=IEEE 802.11                 resources: irq:18 memory:f4500000-f4503fff  
```

using kernel ```
2.6.32-30-generic
``` I use the wireless no problem. It worked out the box. When I use the PAE kernel -35 It will not work. I have googled and tried a variety of fixes. 

I eventually had to remove the pae kernel and run the standard generic. Any advice would be appreciated.

Let me know if you need more outputs.

---

### Post by pinballwizard on 2011-03-14
No-one knows anything? Should I just try 64bit then?

---

### Post by pinballwizard on 2011-03-17
Bump?

No-one using the pae kernel with a broadcom wireless adapter?

---

### Post by nm_geo on 2011-03-17
> **pinballwizard said:**
> Bump?

No-one using the pae kernel with a broadcom wireless adapter?
Yes some do.

```
-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:c1:24:e5
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:efcf0000-efcfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:c5:67:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic-pae firmware=N/A ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg
```However, I could not get the STA driver working but I am happy with the b43 wireless.

---

### Post by pinballwizard on 2011-03-17
> **nm_geo said:**
> Yes some do.

However, I could not get the STA driver working but I am happy with the b43 wireless.

Ok, how did you get it right? I tried for days, and can't get any driver loaded...

---

### Post by false truths on 2011-03-17
The problem could very well have to do with the 2.6.32 PAE kernel. I know for a while I tried to dual-boot Ubuntu 10.04 and Ubuntu 10.10 on my laptop, which has a Broadcom wi-fi card in it, and the drivers just wouldn't work on Ubuntu 10.04 at all. Out of curiosity, I installed the 2.6.35 kernel to 10.04 and it worked just fine.

I've since nuked 10.04 though, due to problems I managed to create in the file system (the entire reason I had two Ubuntu installs to begin with), and I just run the latest stable kernel (2.6.38) in 10.10.

Basically, my suggestion, find and install the latest stable PAE kernel and see if it fixes your problem.

```

sudo add-apt-repository ppa:kernel-ppa/ppa 
```

That repository is a backport of the 10.10 and 11.04 kernels for 10.04.

---

### Post by nm_geo on 2011-03-17
> **pinballwizard said:**
> Ok, how did you get it right? I tried for days, and can't get any driver loaded...

I assume you are running Maverick 10.10 correct ?

The STA driver that you have installed blacklists the B43 driver and ssb.  You will have to fix those before you can install the B43 driver.

Run this code
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The code will tell us if you have blacklisted important driver and support modules.  You could also go to /etc/modprobe.d/ and check all the files for blacklist B43 or blacklist ssb.  If you find those you need to comment the blacklist out by adding # in front of the line example   #blacklist B43.  You will find that you can't edit those unless you are sudo.  The easiest way is to 
```
gksudo gedit /etc/modprobe.d/*
```add the # and save the file/files The two main files to check are blacklist.conf and broadcom-sta-common.conf

Then try to install the firmware-b43-installer and the b43-fwcutter. That has worked for me and others even some Natty testers when a kernel upgrade killed the STA driver.

---

### Post by pinballwizard on 2011-04-01
> **nm_geo said:**
> I assume you are running Maverick 10.10 correct ?

The STA driver that you have installed blacklists the B43 driver and ssb.  You will have to fix those before you can install the B43 driver.

Run this code
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The code will tell us if you have blacklisted important driver and support modules.  You could also go to /etc/modprobe.d/ and check all the files for blacklist B43 or blacklist ssb.  If you find those you need to comment the blacklist out by adding # in front of the line example   #blacklist B43.  You will find that you can't edit those unless you are sudo.  The easiest way is to 
```
gksudo gedit /etc/modprobe.d/*
```add the # and save the file/files The two main files to check are blacklist.conf and broadcom-sta-common.conf

Then try to install the firmware-b43-installer and the b43-fwcutter. That has worked for me and others even some Natty testers when a kernel upgrade killed the STA driver.

Hi, sorry, been away on business.

See as follows:
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
```Running 10.04LTS. 
Should I then install the PAE kernel from 10.10 backports as suggested, or from lucid main? and then un comment the blacklisted items as you say?

---

### Post by arrimapirate on 2011-04-05
Thanks! This fixed it for me. Only question i have is why the hell does it blacklist it in the first place?

---

### Post by bkratz on 2011-04-05
> **arrimapirate said:**
> Thanks! This fixed it for me. Only question i have is why the hell does it blacklist it in the first place?



Well if it did not blacklist it, the two drivers would attempt to each control the card and the conflict would prevent access.

---

