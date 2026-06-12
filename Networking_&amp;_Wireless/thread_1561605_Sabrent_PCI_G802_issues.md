---
title: "Sabrent PCI G802 issues"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by clgy15 on 2010-08-26
Hey everybody,
Well I bought this wireless card because alot of people said it worked out of the box and it almost worked...
Ubuntu recognizes it and the wireless module is activated I just can't seem to scan for networks or connect to them... So I am listing some outputs for you guys and hopefully there is an easy fix.

When I do lspci: I get the following for the card itself
05:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI

When I do ifconfig: I get the following
wlan1     Link encap: Ethernet  HWaddr 00.0c:0a:42:22:d1
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

When I do iwconfig:
wlan1    IEEE 802.11bg ESSID:off/any
            Mode:Managed  Access Point: Not-Associated   Tx-Power=8 dBm
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off

When I do lsmod and find the chipset I get:
rt61pci            18920  0
crc_itu_t          1371   1  rt61pci
rt2x00pci         5995   1  rt61pci
rt2x00lib         27509  2  rt62pci,rt2x00pci
led_class         2864   1  rt2x00lib
mac80211       205146   2  rt2x00pci,rt2x00lib
cfg80211         126517   2  rt2x00lib,mac80211
eeprom_93cx6  1333     1  rt61pci

Then when I do lshw -C netowrk for the wireless I get
description: Wireless interface
product: RT2561/RT62 802.11g PCI
vendor: RaLink
physical id: 2
bus info: pci@0000:05:02.0
logical name: wlan1
version: 00
serial: 00.0c:0a:42:22:d1
width: 32 bits
clock: 33Mhz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: boradcast=yes driver=rt61pci multicast=yes wireless=IEEE 802.11bg
resources: irq:20 memory:fe9f8000-fe9fffff

When I do iwlist scan it says
wlan1 No scan results


My ubuntu version is Ubuntu 10.04.1 LTS
My kernel is 2.6.32-25-generic i686

Please help!

---

### Post by clgy15 on 2010-08-26
Please someone help. Its almost working!!!!! It just feels that something needs to be turned on or something!!

---

### Post by Bluebonze on 2010-10-24
I share your anguish Clgy15.  I recently installed a Sabrent PCI 802N with the same results.  Have you resolved your problem yet?  If so, I would certainly like to hear how.

---

### Post by jrn34exp on 2011-10-22
Looks like I'm not the only one. I, too, cannot get my PCI 802N to work. trying to compile driver RT2860, but all I get is errors. Have either of you solved your problems?

---

### Post by ShirleyTemple on 2013-01-29
I'm going back to Windows:mad:

---

### Post by howefield on 2013-01-29
Old thread closed.

---

