---
title: "weird Broadcom b43 problem"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by stark dar on 2011-02-01
Okay, HP Pavillion dv6000, Ubuntu 10.04.

I downloaded a Broadcom b43 driver after checking that it was right one for my system. It was supposed to show up in System/Admin/Hardware Drivers. it did. I activated it with no results. 
I then rebooted the system, and now it is gone from the Hardware Drivers list. I tried re-entering sudo apt-get install b43-fwcutter

but all it says is that I have the latest version.

How do I activate this driver? I have disabled the presumably wrong Broadcom STA driver that was left in the list.

---

### Post by nm_geo on 2011-02-02
> **stark dar said:**
> Okay, HP Pavillion dv6000, Ubuntu 10.04.

I downloaded a Broadcom b43 driver after checking that it was right one for my system. It was supposed to show up in System/Admin/Hardware Drivers. it did. I activated it with no results. 
I then rebooted the system, and now it is gone from the Hardware Drivers list. I tried re-entering sudo apt-get install b43-fwcutter

but all it says is that I have the latest version.

How do I activate this driver? I have disabled the presumably wrong Broadcom STA driver that was left in the list.

Try to re-install with wired cable and Synaptic first

Give the output of (just copy and paste in the terminal)
```
sudo lshw -C network
```then the output of this long line of commands:(again just copy and paste)
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
```The last one will tell us your blacklisted drivers in the 
(/etc/modprobe.d/) files.

---

### Post by stark dar on 2011-03-23
Hi, I'm having the same problem. 

When I try to re-install it it Synaptic (something I've never done) all I can find in the menu is the b43-fwcutter tool.

Here are the outputs requested:

starkdar@starkdar:~$ sudo lshw -C network
[sudo] password for starkdar: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:b6000000-b6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:f2:23:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
starkdar@starkdar:~$ cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist wl
blacklist uart6850
blacklist twl4030_wdt 
starkdar@starkdar:~$ 

Thanks!

---

