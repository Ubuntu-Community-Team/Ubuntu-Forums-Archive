---
title: "Ralink RT2400 (Linksys WMP54G) - very close, need a little help ..."
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-07-07
As it turns out, I do NOT have an rt2400 chipset.  It's an RT2561/RT61.  Everything works now out of the box.

The kind folks at serialmonkey looked at my pages of error output and suggested it might be a hardware problem.  Just for kicks, I tried taking the card out and putting it in a different slot.  This time it thought it was an IBM card.  I put it back in the slot it was in the first time, now it comes up as an RT2561, which is I think correct for a Linksys WMP54G Rev 4.1.  It loaded the right driver  (rt61pci) this time, and Wicd connected to my WPA2 network without a hitch. :)  

I think the only thing I did when I put it in the second time was I screwed the antenna in tighter.  Anyway, everything's good.  


----------
I have a Linksys WMP54G with a Ralink rt2400 chipset.  I'm running Kubuntu 9.04 64 bit.  I think it's almost working, but not quite.  Here's where things stand now:

lspci
```

05.06.0 Unclassified device [0080]: RaLink Wireless PCI Adapter RT2400 / RT2460 [1814:0101]

```

lshw
```

*-generic
description: Wireless interface
product: Wireless PCI Adapter RT2400 / RT2460
vendor: RaLink
physical id: 6
bus info: pci@0000:05:06.0
logical name: wmaster0
version: 00
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt2400pci latency=32 module=rt2400pci multicast=yes wireless=IEEE 802.11b

```

iwconfig
```

wlan0
IEEE 802.11b ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=20 dBm
(etc)

```

iwlist wlan0 scanning
```

No scan results

```

Wicd doesn't show me any networks.

dmesg has lots of errors like this:

```

phy0 -> rt2400pci_bbp_read: Error - BBCSR register busy. Read failed.
rt2400pci_wait_bbp_ready: Error - BBP register access failed, aborting.
rt2400pci_set_device_state: Error - Device failed to enter state 4 (-5).
failed to set freq to 2462 MGz for scan
failed to restore operational channel after scan

```

If I understand this right, rt2400pci is the "legacy" driver.  I was going to try and get the current rtx00 driver, but it only seems to available as a git tree, etc, meaning that you kind of need internet access in order to be able to get it, and git, and the kernel sources, and so on before you can build it.  If there ever was one thing that should be available as a binary build that you can install without needing any other dependencies, it's network card drivers, no? :lolflag:  but I digress.  

1. Is there another step I need to do to enable this card?

2. Is the rt2400pci driver good for this card, or is the newer driver better?

3. Most of the info I find on the web relies on ndiswrapper, but I shouldn't need that, right?  

thanks!

More:

trying to remove and reload the rt2400pci module, I got this error too:

[code]
rt2400pci_validate_eeprom: Error - Invalid EEPROM data detected.
rt2x00lib_probe_dev: Error - Failed to allocate device.
rt2400pci 0000:05:06.0: PCI INT A disabled
rt2400pci: probe of 0000:05:06.0 failed with error -22

---

