---
title: "Ubuntu 10.04 Ralink 2070 issues"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Bones92 on 2010-06-17
I set up a desktop today and decided to try out linux again, I've tried it in the past before but always gotten deterred by the complex methods one must go through to install drivers. Anyways, I downloaded ndiswrapper onto a different computer and transferred it across and installed, then located a suitable driver for my usb ralink 2070, and then did the whole ndiswrapper -i thing. Now its installed, and ndiswrapper -l reports:

rt2870 : driver installed
device (148F:2070) present (alternate driver: rt2800usb)

iwconfig reports:

wlan0    IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power17 dBm
Retry  long limit: 7  RTS thr:off
Power Management:on

and iwlist wlan0 scan returns:
wlan0   No scan results.

Now I know that there should be scan results, because the computer is a dual boot with 7, and when i boot into 7 it reads a fine 1 bar of reception. 

So any ideas? I'm a bit of a noob when it comes to linux, so clarify all commands as if you were explaining them to a very young small puppy and i'll do my best to follow them :D

---

### Post by Bones92 on 2010-06-17
Wait, I think I installed a 32-bit driver for my 64-bit linux kernel. Will try to remove.

*removes*

*installs 64-bit driver*

Okay, nothing new, all remained the same as above.

I read the advanced ndiswrapper sticky, and did the lshw -C Network

it returned, under the wireless section

*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:0c:43:21:c9:a7
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

Dunno if that helps

---

### Post by Bones92 on 2010-06-20
bump

---

