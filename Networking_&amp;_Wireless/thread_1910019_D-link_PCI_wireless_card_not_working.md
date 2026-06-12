---
title: "D-link PCI wireless card not working"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2012-01-16
Right, obviously I should have done my homework a bit better but here's my situation...

I recently had to move and it's no longer practical for my ubuntu box to be directly plugged into the router. It's a fairly standard not particularly recent viglen box running ubuntu 10.10

I bought a wifi card on ebay. I had hoped it would work out of the box but no wireless capability shows up at all.
I can't figure out how to install drivers for it. Googled around lots and found a site that offered a driver but I had to compile it from source and that never seems to work for me. Also it seemed very old...

On the side of the wifi card it says:
D-Link AirPlus
DWL-520+

When I run lspci this is the only relevant info:

01:02.0 Ethernet controller: Texas Instruments ACX 100 22Mbps Wireless Interface
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

I presume the realtek controller is the onboard wired ethernet.

iwconfig shows:

lo        no wireless extensions.

eth0      no wireless extensions.

I don't think it's worth filling this up with all the other stuff suggested in the sticky about wireless problems as it seems clear I just need drivers... If I'm wrong please feel free to tell me! It might take a little while to get round to posting results as I have to physically move this particular computer into my housemate's room along with CRT screen and keyboard to plug it into the router to get it online!

---

### Post by praseodym on 2012-01-16
Hi,

this driver **acx** is no longer part of the kernel since 9.10. You need to install ndiswrapper and use the driver attached. It only works IMHO with WPA(1). Is it 32 or 64bit? For 64bit you need to compile ndiswrapper with a patch

---

### Post by mistafeesh on 2012-01-16
32-bit. Thanks very much! I'll get onto it and let you know how I got on.

---

