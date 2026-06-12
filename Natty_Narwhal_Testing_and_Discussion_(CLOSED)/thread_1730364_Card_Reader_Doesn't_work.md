---
title: "Card Reader Doesn't work"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2011-04-15
The card reader in my laptop doesn't work in natty. I was able to get it to work in maverick by creating toshib_sd_reader.conf in /etc/modprobe.d and adding options sdhci debug_quirks=0x40 and then rmmod/modprobe sdhci_pci and sdhci as stated here: [URL="http://ubuntuforums.org/showthread.php?t=1544350"]http://ubuntuforums.org/showthread.php?t=1544350
[/URL] 
However, in Kubuntu Natty this doesn't work.

Here's the info related to the reader:
```
07:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) (prog-if 01)
        Subsystem: Toshiba America Info Systems Device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0503800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

07:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
        Subsystem: Toshiba America Info Systems Device ff50
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f0502000 (32-bit, non-prefetchable) [size=4K]
        Memory at f0503000 (32-bit, non-prefetchable) [size=2K]
        Memory at f0500800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
```Any ideas?

---

