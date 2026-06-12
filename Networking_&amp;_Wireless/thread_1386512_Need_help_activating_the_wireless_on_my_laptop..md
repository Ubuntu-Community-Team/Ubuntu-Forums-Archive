---
title: "Need help activating the wireless on my laptop."
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by Ruskiy Letenant on 2010-01-20
This must be a repost, but I still want to ask, how do I activate the wireless on my laptop? I've been given advice about this a while back, but forgot. Just reinstalled a fresh copy of 9.10 so need some help.

Or is there an alternative way to do this?

---

### Post by teward on 2010-01-20
We need more info, such as the specific wifi card.

Do this command in terminal:
```
lspci
```
and post output here.  we're specifically looking for your network controllers.

---

### Post by Xog on 2010-01-20
I'm having the same problem. (using desktop btw)
```

xog@xog-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:01.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
02:03.0 PCI bridge: nVidia Corporation Device 05bf (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
09:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

it's a usb so:
```

xog@xog-desktop:~$ lsusb
Bus 002 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Ruskiy Letenant on 2010-01-20
Network Card:

**[COLOR=Red]Broadcom Corporation BCM4311 802.11b/g WLAN[/COLOR]**

---

### Post by PRC09 on 2010-01-20
For Broadcom cards.....

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

And this as well....

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by teward on 2010-01-20
> **Xog said:**
> I'm having the same problem. (using desktop btw)
]it's a usb so:
```

xog@xog-desktop:~$ lsusb
Bus 002 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 1737:0077 Linksys **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Your issue, Xog, is a bit different, as the device only shows up as "Linksys" (bolded above).

Might I recommend you post the quote above and your issue in another thread, and you provide details there of what Linksys wifi adapter you have?

---

### Post by Xog on 2010-01-20
> **TrekCaptainUSA said:**
> Your issue, Xog, is a bit different, as the device only shows up as "Linksys" (bolded above).

Might I recommend you post the quote above and your issue in another thread, and you provide details there of what Linksys wifi adapter you have?

Already did.

---

### Post by Ruskiy Letenant on 2010-01-21
Well, that solved all my wireless problems, **[COLOR=Red]THANK YOU![/COLOR]**

---

