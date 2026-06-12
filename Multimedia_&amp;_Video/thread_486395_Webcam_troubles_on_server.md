---
title: "Webcam troubles on server"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Sikarian on 2007-06-28
I've connected my creative notebook pro cam to my 7.04 server edition box.

It wasnt detected automatically, I've downloaded and installed the drivers (make, make install, etc) and that didnt give me any errors at all.

When I hook up the camera, the light comes on, and lspci shows nothing.

Here's the latest reports from dmesg
```

[  542.246075] usb 1-2: new full speed USB device using uhci_hcd and address 4
[  542.425302] usb 1-2: configuration #1 chosen from 1 choice
[  542.428268] /home/administrator/gspcav1-20070508/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[  542.428292] /home/administrator/gspcav1-20070508/gspca_core.c: [spca5xx_probe:4098] Camera type JPEG 
[  542.428310] /home/administrator/gspcav1-20070508/Vimicro/zc3xx.h: [zc3xx_config:515] Sensor ID:22
[  543.212732] /home/administrator/gspcav1-20070508/Vimicro/zc3xx.h: [zc3xx_config:522] Find Sensor Tas5130 (VF0250)
[  543.216026] /home/administrator/gspcav1-20070508/gspca_core.c: [spca5xx_getcapability:1215] maxw 640 maxh 480 minw 176 minh 144
[  707.797960] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7
[  708.157897] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7
[  718.726230] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7
[  729.674485] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7
[  740.612755] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7
[  751.551020] /home/administrator/gspcav1-20070508/gspca_core.c: [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7

```

heres the output from lspci

```
[administrator@athena:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:13.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 22)

```



I'm not really sure what's going on.  

Quick edit:  /dev/video0 is there...I'm trying to use Zoneminder if that helps any.  
Any ideas?

I can setup Zoneminder to use /dev/video0 as a source, and it's not red like the ZM manual says it would be if there was a problem, but when I open it up, no video, zilch, and it says idle.  I just have a feeling the cam isnt being detected

---

### Post by Sikarian on 2007-06-28
DMESG continues to spam that /home/administrator/gspcav-20070508/gspca_core.c [gspca_set_isoc_ep:903] ISO EndPoint found 0x81 AlternateSet 7

over and over.  That last entry I posted had like, 740-751 as the number before the error.

Dmesg is now at 47662.632605.

---

