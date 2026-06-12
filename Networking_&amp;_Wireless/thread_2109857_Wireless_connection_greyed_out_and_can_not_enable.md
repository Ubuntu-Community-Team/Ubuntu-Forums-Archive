---
title: "Wireless connection greyed out and can not enable"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by divishal on 2013-01-28
I fresh installed ubuntu 12.10 on my Sony Vaio laptop VGN-N130g

The inbuilt wireless card was not active so I thought of installing a separate usb wifi card Its my bad luck or lack of knowledge that I can' make either of the wireless card active. They are turned grey, and futher states that wireless is disabled by hardware switch.  Need to mention there is switch for internal card, switching  on and off doesn't do anything.

Below is the output from lshw -C NETWORK

 *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:26:d1:13
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-21-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:da000000-da000fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan1
       serial: 00:0b:81:85:3f:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated

---

### Post by ahallubuntu on 2013-01-28
Even if you could get the USB dongle recognized, the built-in driver in 12.10 is broken and you'd need to build the latest driver from Realtek, anyway (for "RTL8192CU"). If recognized, you'd see a list of wireless networks the dongle is picking up but you'd have trouble connecting.

But in your case, I think wireless is disabled because of something else.  Normally Intel cards work automatically, but I believe something with the laptop is confusing Ubuntu into not allowing it to be enabled.  Unable to sense that switch properly?  (I think if you disable the internal card with that switch it will disable ALL wireless in Linux.)

This page offers some tips you could try:

[http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error](http://askubuntu.com/questions/139036/how-do-i-fix-a-wireless-is-disabled-by-hardware-switch-error)

---

