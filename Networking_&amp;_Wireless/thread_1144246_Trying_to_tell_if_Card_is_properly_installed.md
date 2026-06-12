---
title: "Trying to tell if Card is properly installed"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by jskill23 on 2009-04-30
Hi, I just installed Ubuntu 9.04 last night and am playing around with getting my encore ENLWI-G2 wireless card.  I looked around these forums and found that the driver is supposed to be on the default load so I was told to type this into a terminal:

sudo lshw -C network
Here is the output :

*-network
      description: Ethernet controller
      product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: 7
      bus info: pci@0000:01:07.0
      version: 20
      width: 32 bits
      clock: 33MHz
      capabilities: pm cap_list
      configuration: driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180

*-network DISABLED
      description: Ethernet interface
      physical id: 1
      logical name: pan0
      serial: 26:cc:18:be:85:6a
      capabilities: ethernet physical
      configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
link=yes multicast=yes


There may be some misspellings because I am copying it from one screen to another.  I am unsure if that means it is installed correctly or not.  When I type in iwconfig I get:

lo           no wireless extensions
eth0       no wireless extensions
pan0      no wireless extensions


I am confused as to where to go from here.  It does not show up any wireless networks that I can see.  Can anyone steer me in the right way?

Thanks

---

