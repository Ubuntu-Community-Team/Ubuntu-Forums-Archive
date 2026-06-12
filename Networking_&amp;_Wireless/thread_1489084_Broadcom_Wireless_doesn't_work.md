---
title: "Broadcom Wireless doesn't work"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by wasabishot on 2010-05-20
Hello

I'm working on Lucid, in HP Pavilion 9730us laptop.

My wireless broadcom card was working just fine until now as i installed it with the Hardware Devices manager,
Today i put a new ALFA AWUS036H usb card to work with aircrack.
both cards were working together for a while, but as i started playing around with aircrack the broadcom card of the HP has stopped working.

Of stupidity i made a mistake and followed the aircrack tutorial for R8187 / ieee80211 stacks driver, while i'm using RTL 8187 / mac80211 stack drivers, and blacklisted the RTL8187 , rebooted and then both  card didn't work. I un-blacklisted it, and the ALFA is working but the broadcom not!!

iwconfig shows me only one wireless card on wlan0
the blue light showing activity in the HP card doesn't go on.

tried to uninstall and reinstall broadcom drivers, still no change.

Any idea what should i do???
I don't want to use the usb card regularly...   

any help will be very appreciated!!!!

---

### Post by wasabishot on 2010-05-21
Another thing to mention:

lspci does recognize my unworking card
last line:

```

```
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

```

and output of : sudo lshw -C network:

```

```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:07:d4:10
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f2588000-f2588fff ioport:30f8(size=8) memory:f2589c00-f2589cff memory:f2589800-f258980f
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f2200000-f2203fff memory:f2000000-f20fffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:c0:ca:3e:d0:cb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.32-22-generic firmware=N/A ip=192.168.0.199 link=yes multicast=yes wireless=IEEE 802.11bg
```

```

any help guys???????????

---

### Post by wasabishot on 2010-05-21
fixed the problem with:

```

``` $ sudo apt-get remove  --purge linux-backports-modules-*```

```

then went to Hardware drivers, uninstall Broadcom STA wireless driver, then activated it, rebooted and voiala!!! both cards are working together...


happy end, love you ubuntu

---

