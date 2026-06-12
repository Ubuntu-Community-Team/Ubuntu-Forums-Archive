---
title: "wireless help please"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by grendel38 on 2006-04-11
So far my experience with Ubuntu linux has been good, with one large glitch.  No matter what I do I can't get wireless to work.

I have a d-link dwl-650 and a dwl-650+ card.

I have a dual boot Ubuntu 5.10 and Windows XP system.  Both cards work flawlessly in Windows, as much as it pains me to say it.

Ubuntu doesn't seem to recognize the 650 card at all.  when I run "cardctl ident" no information comes back for the card.

the 650+ card is recognized.  cardctl ident gives

[INDENT] product info: "Wireless Network CardBus PC Card", "Global", "", ""
  manfid: 0x0097, 0x8402
  function: 6 (network)
[/INDENT]

lshw gives:

 description: Wireless interface
          product: ACX 100 22Mbps Wireless Interface
          vendor: Texas Instruments
          physical id: 0
          bus info: pci@05:00.0
          logical name: wlan0
          version: 00
          serial: 00:0d:88:80:3c:2a
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+
          resources: ioport:4800-481f iomemory:11010000-11010fff iomemory:11000000-1100ffff irq:11

from what I've read the card does use a acx100 chip so it looks like the correct driver is installed.

But I can't connect with it.  "iwlist scan" gives "no scan results"  even when I can switch to Windows and find a router right away.

I've installed ndiswrapper and the windows driver for the card.  ndiswrapper says the hardware is present, but I still can't connect.  ](*,) 

One question:  with ndiswrapper installed should I still get the message that the card is using the acx_pci driver?  That's the native linux driver for the card.  Shouldn't it be using the windows driver instead?

Any help would be appreciated.  I'd really like to ditch windows, but I can't until I get wireless up and running.

Oh, I can get wired ethernet no problem.

---

### Post by karthik085 on 2006-04-12
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

---

### Post by pr0x on 2006-04-12
hi mate try this link it works perfect [http://www.linuxresource.co.uk/index.php?module=tutorials&display=36](http://www.linuxresource.co.uk/index.php?module=tutorials&display=36)

---

