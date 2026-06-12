---
title: "Wireless Trouble"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by TheTwilit on 2009-12-13
Hello,

Ubuntu is currently unable to run wireless on my laptop.  I have a MacBook Pro 15.4":

Here's my specs:

OS: Mac OS X Snow Leopard (10.6.2) / 25.7 GB of Ubuntu 9.10 (Hard drive capacity is 500 GB 7200 rpm)
Graphics card: 2 NVIDIA cards (NVIDIA GeForce 9400M and NVIDIA GeForce 9600M GT) 256 MB
Memory: 4GB 1066MHz DDR3 SDRAM - 2x2GB
Processor: 1 Intel Core 2 Duo 2.66 GHz (3MB L2 cache)

When running lspci -n, I get:
```

00:00.0 0600: 10de:0a82 (rev b1)
00:00.1 0500: 10de:0a88 (rev b1)
00:03.0 0601: 10de:0aae (rev b3)
00:03.1 0500: 10de:0aa4 (rev b1)
00:03.2 0c05: 10de:0aa2 (rev b1)
00:03.3 0500: 10de:0a89 (rev b1)
00:03.4 0500: 10de:0a98 (rev b1)
00:03.5 0b40: 10de:0aa3 (rev b1)
00:04.0 0c03: 10de:0aa5 (rev b1)
00:04.1 0c03: 10de:0aa6 (rev b1)
00:06.0 0c03: 10de:0aa7 (rev b1)
00:06.1 0c03: 10de:0aa9 (rev b1)
00:08.0 0403: 10de:0ac0 (rev b1)
00:09.0 0604: 10de:0aab (rev b1)
00:0a.0 0200: 10de:0ab0 (rev b1)
00:0b.0 0101: 10de:0ab5 (rev b1)
00:0c.0 0604: 10de:0ac4 (rev b1)
00:15.0 0604: 10de:0ac6 (rev b1)
00:16.0 0604: 10de:0ac7 (rev b1)
02:00.0 0300: 10de:0647 (rev a1)
04:00.0 0280: 14e4:432b (rev 01)
05:00.0 0c00: 11c1:5901 (rev 07)

```

And when running lspci:

```
nick@nick-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)


```

The OS is also not detecting my hardware, and I think I've found why, but I need to have the wireless installed.

What do I do?

~Twilit

---

### Post by bkratz on 2009-12-13
Yours is the BCM4322 have a look at this thread especially post #10



Forgot the thread!!

[http://ubuntuforums.org/showthread.php?t=1312603&highlight=BCM4322](http://ubuntuforums.org/showthread.php?t=1312603&highlight=BCM4322)

---

### Post by TheTwilit on 2009-12-15
> **bkratz said:**
> Yours is the BCM4322 have a look at this thread especially post #10



Forgot the thread!!

[http://ubuntuforums.org/showthread.php?t=1312603&highlight=BCM4322](http://ubuntuforums.org/showthread.php?t=1312603&highlight=BCM4322)

I don't have a wired internet connection, though.

---

