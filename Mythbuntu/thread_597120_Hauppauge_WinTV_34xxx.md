---
title: "Hauppauge WinTV 34xxx"
date: 2007-10-30
forum: Mythbuntu
---

### Post by crobinson55331 on 2007-10-30
Not able to properly set up this capture card on mythbuntu 7.10.  dmesg returns the following about the card
[   37.352792] CORE cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected]
[   37.352796] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   37.520955] tveeprom 2-0050: Hauppauge model 34132, rev J158, serial# 2956516
[   37.520960] tveeprom 2-0050: tuner model is Philips FM1236 MK3 (idx 58, type 43)
[   37.520964] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   37.520967] tveeprom 2-0050: audio processor is CX880 (idx 30)
[   37.520969] tveeprom 2-0050: has radio
[   37.520972] cx88[0]: warning: unknown hauppauge model #34132
[   37.520974] cx88[0]: hauppauge eeprom: model=34132
[   37.532888] input: cx88 IR (Hauppauge WinTV 34xxx  as /class/input/input4
[   37.532938] cx88[0]/0: found at 0000:02:07.0, rev: 5, irq: 17, latency: 32, mmio: 0xfb000000
[   37.611648] tuner 2-0043: chip found @ 0x86 (cx88[0])
[   37.611689] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   37.613398] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   37.613409] tuner 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   37.613412] tuner 2-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   37.615725] cx2388x alsa driver version 0.0.6 loaded
[   37.625412] cx88[0]/0: registered device video0 [v4l2]
[   37.625442] cx88[0]/0: registered device vbi0
[   37.625480] cx88[0]/0: registered device radio0

I get programming error when I try and scan for channels.  Any help would be appreciated.

---

### Post by crobinson55331 on 2007-10-31
Can antone help?

---

