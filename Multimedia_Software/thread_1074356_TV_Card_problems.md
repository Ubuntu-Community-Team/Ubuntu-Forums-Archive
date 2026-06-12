---
title: "TV Card problems"
date: 2009-02-19
forum: Multimedia Software
---

### Post by vistar86 on 2009-02-19
Hi i have a DVD/Analogue Hybrid TV card (which worked in windoze) it seems the driver saa7134 but shows as unknown in programs.

How do i get programs to use this card, i currently use VLC but have Myth TV/TV Time/Elisa/Kaffeine installed, which ever's easiest for anybody to explain :)

_Heres the lspci -v info:_

04:04.0 Multimedia controller: Philips Semiconductors **SAA7131/SAA7133/SAA7135** Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Device 2d01
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: saa7134
        Kernel modules: **saa7134**


_With dsmeg i get the following:_

[   12.720946] Linux video capture interface: v2.00                                                     
[   12.742182] usb 2-2: reset full speed USB device using uhci_hcd and address 4                        
[   12.853384] saa7130/34: v4l2 driver version 0.2.14 loaded                                            
[   12.853451] saa7134 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                         
[   12.853460] saa7133[0]: found at 0000:04:04.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdbfe000      
[   12.853469] saa7133[0]: subsystem: 1461:2d01, board: UNKNOWN/GENERIC [card=0,autodetected]           
[   12.853480] saa7133[0]: board init: gpio is 0  


Heres a screenie of Myth TV setings too:

[IMG]http://i220.photobucket.com/albums/dd224/bren1986/snapshot6.png[/IMG]

Hope somebody can help :)

---

