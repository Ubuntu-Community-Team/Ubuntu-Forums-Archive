---
title: "Randomly can't reach Ubuntu box thru web or SSH"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by ledzepp817 on 2011-11-02
Hello everyone,
 
I am running a 10.10 box that I host an apache2 web server on. It is thru a wireless connection because a wired connection is not an option. At random times, I can't access any web pages from it. But I also can't SSH to it neither. I know the box is up, I know my wireless network is fine, but it just seems that the wireless card is unavailable at certain times. If I am sitting locally at the machine, I have never had a connectivity problem, just when i try to get to it remotely.
 
Things I've tried:
1.) I removed Network Manager and installed Wicd. This seemed to reduce the amount of "hangups" but they are still there.
2.) I've looked at all the logs in the /var/log dir. The only events I see during the time of unavailability are postfix/cron jobs. Could these be disabling/taking over the wireless card?
3.) Just did a recent update thru Ubuntu, so recently patched 10.10. still no help.
 
So I am kinda stuck here and hope a ninja in this forum can help. I just have no idea if its a kernel issue, a driver issue, a hardware issue, a config issue, a user issue, etc.
 
Any help would be greatly appreciated. Thanks all!
 
Some info if it helps:
 
$uname -a
Linux Desktop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux
 
$lshw
*-network
description: Wireless interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: 7
bus info: pci@0000:01:07.0
logical name: wlan0
version: 00
serial: 00:21:29:e9:55:f3
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-generic firmware=N/A ip=192.168.211.105 latency=64 link=yes multicast=yes
wireless=IEEE 802.11bg
resources: irq:19 memory:dfff8000-dfffffff

---

### Post by ledzepp817 on 2011-11-08
Still having the issue.  Last shot for any advice.  Thanks!

---

