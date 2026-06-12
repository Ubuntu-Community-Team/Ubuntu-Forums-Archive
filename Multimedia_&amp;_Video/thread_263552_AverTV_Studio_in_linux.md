---
title: "AverTV Studio in linux"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by tosun pasa on 2006-09-23
I'm new in linux.I wonder can i use my tvtuner(AverTV Studio 303 ) in linux or not?

---

### Post by alex.scotton on 2007-10-26
er... Yeah me too! I have the AverTV 303p Studio and am trying to use MythTV but don't even know whether there are drivers installed... here's my lspci read out:

```
 00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:06.0 USB Controller: NEC Corporation USB (rev 43)
00:06.1 USB Controller: NEC Corporation USB (rev 43)
00:06.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
***** 00:07.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01) *****
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```
I think it's the one i have starred, obviously starting with the obvious that my card is Aver media, and it's reading as a phillips video broadcast decoder, i'm simply going to assume that it has a phillips chipset!

Anyways, if anyone can help me figure out whats going on then it would be much appreciated!

Alex

---

### Post by freakavoid on 2007-12-21
I just got it working under gutsy (averTV 303) if anyone still needs it this is how i did it:

```

sudo modprobe cx88xx card=6
sudo modprobe cx8800

```

---

