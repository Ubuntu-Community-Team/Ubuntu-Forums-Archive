---
title: "Nebula DigiTV PCI not recognised on Ubuntu 7.04"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by luckyjonny on 2007-06-17
I wonder if anyone here could shed some light on this problem. I'm currently trying to set up a MythTV box using a DigiTV PCI card with a M45P8-MLF motherboard. I followed [this](http://www.parker1.co.uk/mythtv_ubuntu.php) guide, only to get the ```
myth tv could not open card #0
``` 
message when trying to set up the mythtv backend.

I tried ```
sudo modprobe -v dvb_bt8xx
``` 
and then tried using Kaffeine, but DVB was not detected. I searched these forums, but can't seem to find a problem quite like mine. Something in the output of dmesg caught my eye, but I'm not really sure where to go from here. I'm wondering whether the riser card the DigiTV card is plugged into in order to fit into the case could be the root of the problem? Or maybe that the motherboard is just a little too obscure? Any help would be most gratefully received. Here's the bit of dmesg that looked worrying:

```
[   42.543384] bttv: driver version 0.9.16 loaded
[   42.543389] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   42.543479] bttv: Bt8xx card found (0).
[   42.543502] ACPI: PCI Interrupt 0000:02:05.0[?] -> GSI 19 (level, low) -> IRQ 16
[   42.543509] bttv0: can't request iomem (0x0).
[   42.543515] bttv: probe of 0000:02:05.0 failed with error -16
```

lspci results in:

```
lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP PCI/AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc Unknown device 4367 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc Unknown device 4368 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc Unknown device 4365 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 03)
00:14.1 IDE interface: ATI Technologies Inc Unknown device 4369 (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 436c (rev 01)
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4362 (rev 01)
00:14.5 Multimedia audio controller: ATI Technologies Inc Unknown device 4361 (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 9100 PRO IGP
02:05.0 Class ffff: Brooktree Corporation Bt878 Video Capture (rev 10)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```

---

