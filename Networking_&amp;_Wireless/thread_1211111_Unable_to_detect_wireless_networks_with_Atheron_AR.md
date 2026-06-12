---
title: "Unable to detect wireless networks with Atheron AR242x"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by skipkirk on 2009-07-12
So here's my problem. I installed 9.04 from a CD and haven't been able to detect any wireless connections. While I was testing it directly from the CD, Ubuntu did manage to see other connections. After installation, I couldn't see them anymore. 

I've tried using ndiswrapper but it doesn't work. I will troubleshoot using the sticky tomorrow but for now I've posted information below. I'm on another PC connected wireless to the Internet as well. I won't be able to connect my laptop via wire since I don't own one, and anyway that beats the purpose of a laptop. Hope to get some help as I'm really new to Ubuntu. Thanks in advance

**1 ) Laptop Brand**
     
     An ASUS F5RL

**2 ) Wireless Brand, Model and Wireless Chipset:**
     

    > Atheros Comm Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[B]

3 ) check interface:[/B]
     > 
     wlan 0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.412 GHz Access Point:Not-Associated
Bit Rate: 54 Mb/s
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0     [B]

5 ) Kernel boot messages[/B]

> dmesg [-c] [-n level] [-s bufsize] [B]
6 ) Network configuration[/B]
     
     > *-network
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: 00:15:af:54:bc:4f
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast = yes driver=ndiswrapper+net5211 driverversion=1.53+,06/21/2007,5.3.0.56 
latency=0 module=ndiswrapper multicast=yes wireless=IEEE 80211.g[B]
7 ) Scan for networks:[/B]
     
     > wlan0 No scan results [B]

8 ) Ubuntu Version: [/B]
     
> 9.04 [B]

9 ) Kernel/architecture (including 32 vs. 64 bit): [/B]
     
     > 2.6.28-11-generic i686 [B]

10 ) Restarting the network:[/B]
     
> WARNING: ifup -a is disabled in favour of Network Manager
Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.

---

### Post by superprash2003 on 2009-07-12
aptops come with a wireless switch, which has an ON/OFF button or a keyboard shorcut.. make sure that the wifi switch is ON.. 

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by skipkirk on 2009-07-12
Thanks for the reply

Yeah, the switch is turned on. I've frustratingly turned it off and on to no avail.

---

