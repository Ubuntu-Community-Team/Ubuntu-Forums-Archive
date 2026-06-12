---
title: "Ralink wireless card won't enable since updating kernel to 2.6.35-24 in Maverick"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by Vermilion Sparrow on 2010-12-26
Actually, the title is a bit misleading. I'm used to having to reinstall the Ralink drivers every kernel update, but the last kernel update (2.6.35-23) it just worked--for once. What happened this time, however, is much more difficult to pinpoint.

I installed updates, which included the kernel update 2.6.35-24, on the morning of the 24th and then shut down the laptop to go to my dad's for Christmas. When I arrived that evening, I booted up the laptop and was able to connect to his wireless network to check my email, then shut down the laptop again before going to bed.

At this point, I will admit that I closed the laptop before the shutdown sequence was finished, which is something I don't normally do, but as far as I'm aware shouldn't have caused any problems. However...

The next day I needed to check something, so I turned the laptop on again and was met with "wireless is disabled" in the connection menu. The hardware switch is a function key, so couldn't have been touched. I rebooted a couple times (even switched to the old kernels I still have installed) with no luck, but ultimately decided I could wait until I got home to fix it.

So I'm home now, and I've re-downloaded and re-compiled the manufacturer's driver from their website, which is what I've done in the past when a kernel update breaks my wireless, and this hasn't helped.

Since I've had recurring problems with my Ralink RT3090 card, I have the usual blacklist entries (rt2860sta, rt2870sta, rt2800pci, rt2800lib, rt2800usb rt2x00pci, rt2x00lib, rt2x00usb) already in place in /etc/modprobe.d/blacklist.conf. I have all of these blacklisted because before I did so, the laptop would freeze anytime I tried to shut down, restart, hibernate, or sleep.

Oh, and...

```
~$ uname -r
2.6.35-24-generic

~$ lspci -v
01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Micro-Star International Co., Ltd. Device 6891
        Physical Slot: 0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fe900000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt3090sta, rt2860sta, rt2800pci

~$ lsmod | grep -e rt2 -e rt3
rt3090sta             913613  0
cfg80211              144470  1  rt3090sta

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA

~$ dmesg | grep -e rt2 -e rt3
[    7.675227] rt2860 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.675316] rt2860 0000:01:00.0: setting latency timer to 64
```

**EDIT:** Argh, never mind. I got annoyed and toggled the hardware switch a few times and it finally enabled. I won't be closing this laptop before the shutdown is complete ever again!

---

