---
title: "CyberTV w/  Conexant CX23880 setup"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by bolivartech on 2008-04-14
I'm trying to set up my PC to play TV through it using this CyberTV w/  Conexant CX23880 card. It isn't auto detected and wasn't on the list in the dmesg so I set it to UNKNOWN/GENERIC [card=0,insmod option]. Now the dmesg reads

[   33.199033] Linux video capture interface: v2.00
[   33.712929] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   33.713003] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   33.713093] cx88[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,insmod option]
[   33.713098] cx88[0]: TV tuner type -1, Radio tuner type -1
[   33.834080] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   33.834098] cx88[0]/0: found at 0000:00:09.0, rev: 5, irq: 19, latency: 32, mmio: 0xfa000000
[   34.225307] All bytes are equal. It is not a TEA5767
[   34.225315] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   34.225476] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   34.279079] cx88[0]/0: registered device video0 [v4l2]
[   34.279106] cx88[0]/0: registered device vbi0
[   34.279121] tuner 0-0060: tuner type not set

It appears to be found by kdetv, vlc player, tvtime, etc. But I'm stumped at this point. If I get it set right, or so I think I get a fuzzy screen which seems like progress but where do I go from there? I know I won't have sound yet because I haven't put in a cable from the tuner to the sound card but I'd settle for a picture. Also if it matter I'm getting the signal from a dish tuner, not from the satellite but actually on TV 2 out. Any help would be much appreciated![-o<

---

### Post by bolivartech on 2008-04-14
It seems to be that the tuner itself is not working. I'm going to attempt to hook something up to composite or s-video tomorrow and see for sure though. How do I set the tuner type?:confused:

---

### Post by bolivartech on 2008-04-14
As a second thought, before I kill myself making this work would someone reccomend an inexpensive card that definetly works well? Mostly for viewing, and the occasional copy to DVD(like once a month) Thanks! This one didn't cost me any.

---

