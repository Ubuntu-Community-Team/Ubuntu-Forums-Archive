---
title: "&quot;No devices detected&quot; after specifying &quot;via&quot; driver in xorg.conf"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by jeeves on 2006-06-25
I'm trying to take advantage of my newly compiled via drivers by editing my xorg.conf. However whenever I do this X will not start and I get a **"no screens found"** error. Here is an excerpt from the end of my Xorg.O.old.log:

```
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400
(II) Primary Device is: PCI 01:00:0
**(EE) No devices detected.**

Fatal server error:
**no screens found**
```

Any idea on how to fix this (aside from changing it back to vesa)?

One possible cause is that the kernal is not recognizing the onboard video. Here are the results of from running **lspci** (note the "Unknown Device" under VGA compatible controller:

0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:00:0c.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:00:0c.3 0805: Texas Instruments: Unknown device 803c
0000:00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
**0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)**

---

### Post by calinb on 2006-06-28
I just went through this with my FC5-64 Openchrome driver install.  It looks like your driver isn't loading.

modprobe -a via

and a reboot did the trick, as I recall.  However, my kernel doesn't recognize the 0x3344 PCI device ID either and I get the same "Unknown Device" message.

---

