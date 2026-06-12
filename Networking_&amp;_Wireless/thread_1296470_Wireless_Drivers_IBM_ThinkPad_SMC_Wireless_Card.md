---
title: "Wireless Drivers IBM ThinkPad SMC Wireless Card"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by ZER01NE1NE on 2009-10-20
Hi all,

I'm setting up Ubuntu 9.04 Jaunty on an IBM ThinkPad with wireless card WL541C manufactured by SMC. I can't figure out how to get Ubuntu to recognize the card. Does Ubuntu come with drivers for this card, or do I have to download them myself? Thanks in advance.

~ Kyle

---

### Post by t0mppa on 2009-10-20
Open up a terminal, run **lshw -C network** and post the output here. If your system recognizes the card, it will be listed there. It will also show us what drivers (if any) are getting associated with it.

---

### Post by ZER01NE1NE on 2009-10-20
> **t0mppa said:**
> Open up a terminal, run **lshw -C network** and post the output here. If your system recognizes the card, it will be listed there. It will also show us what drivers (if any) are getting associated with it.

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:09:6b:bf:5d:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 00:50:18:37:56:98
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:99:0f:18:aa:df
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by t0mppa on 2009-10-21
Ooh, a Texas Instruments chip, don't see those everyday. Anyway, it looks like the card is recognized and a driver is assigned correctly. Try running a **sudo iwlist scan** to see, if it can pick up any networks.

The documents that I found suggest that you'd need to disable Network Manager in order to get this driver to work, but since it's an older card, the instructions are for 7.04 and 7.10 and it's not mentioned whether this still applies to later versions of Ubuntu (and Network Manager). You can read more from the [Ubuntu help wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111") or [the driver wiki pages]("http://acx100.sourceforge.net/wiki/Main_Page").

---

