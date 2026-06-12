---
title: "[Broadcom 4311] Network Controller has no logical name"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by roperp on 2011-05-26
I've just begun with a fresh USB install of Ubuntu 11.04, and have run into the seemingly standard wireless network issue with the Broadcom 4311. I've read countless posts on this forum, and have installed the STA driver "proprietary..." through the GUI driver installer.

Here is the latest from my lshw:
~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
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
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:76:36:04
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.9 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

It would appear that my wireless network connection has no logical name, which may be at the root of some problems.

To check my "rfkill" as seems popular to do with network bugs:

~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Previously, it was "Soft blocked: yes" but I've frantically entered several commands in the terminal, ranging from "rfkill unblock all" to "cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'"

The usual symptoms seem to persist; I can connect to the network using my wired connection, but when I unplug no wireless network connections kick in, or show up, or seem to be responsive anywhere...

Also, I should note that I've read the forum post [HERE]("http://ubuntuforums.org/showthread.php?t=1156775") but without much further understanding or resolution.

Thanks for the help.

---

### Post by nm_geo on 2011-05-26
Okay lets look at the following

```
lspci -nn
```The the output of this one too.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```That long last one gives us the blacklisted drivers. i have a feeling you have ssb blacklisted (just a feeling we will see)

---

### Post by roperp on 2011-05-27
Woot! Sorry to be negligent, but I just *knew* someone else had to have had this problem. I found someone else with the problem, and that thread had the problem.

The solution to my problem was at:

[http://ubuntuforums.org/showpost.php?p=10778618&postcount=25](http://ubuntuforums.org/showpost.php?p=10778618&postcount=25)

---

### Post by nm_geo on 2011-05-27
> **roperp said:**
> Woot! Sorry to be negligent, but I just *knew* someone else had to have had this problem. I found someone else with the problem, and that thread had the problem.
 
The solution to my problem was at:
 
[http://ubuntuforums.org/showpost.php?p=10778618&postcount=25](http://ubuntuforums.org/showpost.php?p=10778618&postcount=25)
 
You did good roperp to mark solved and provide link to resolution.  Jospeh will be pleased as well.

---

### Post by josephmills on 2011-05-27
I am pleased to see that it is working great! Have fun with your wireless and ubuntu ):P

---

