---
title: "Can't change tv card tuner"
date: 2011-02-20
forum: Multimedia Software
---

### Post by razan on 2011-02-20
Hi! I have 2 tv cards that I have successfully configured to work in linux.But this 3rd one I bought recently seems to have a problem. The card is not autodetcted (that's really not the problem) but when I try to load saa7134 with:

sudo modprobe saa7134 card=xx tuner=xx

, it loads whatever card I indicate but the tuner never changes. This is part of the output of dmesg:


Linux video capture interface: v2.00
saa7130/34: v4l2 driver version 0.2.15 loaded
saa7134 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
saa7130[0]: found at 0000:02:04.0, rev: 1, irq: 16, latency: 66, mmio: 0x40100000
saa7130[0]: subsystem: 1131:0000, board: Sabrent SBT-TVFM (saa7130) [card=42,insmod option]
saa7130[0]: board init: gpio is 804000
IRQ 16/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Intel ICH 0000:00:1f.5: setting latency timer to 64
saa7130[0]: Huh, no eeprom present (err=-5)?
i2c i2c-1: Invalid 7-bit address 0x7a
tuner 1-0060: chip found @ 0xc0 (saa7130[0])
tea5767 1-0060: type set to Philips TEA5767HN FM Radio
saa7130[0]: registered device video0 [v4l2]
saa7130[0]: registered device vbi0
saa7130[0]: registered device radio0


It doesn't matter whatever tuner I try to load, the output is

tea5767 1-0060: type set to Philips TEA5767HN FM Radio.

What can I do to override this default tuner?

It's a lightwave TV/FM analogue card. But it's really a clone of a Sabrent SBT-TVFM card. 

This is the relevant output of lspci -vnn:

02:04.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
    Subsystem: Philips Semiconductors Device [1131:0000]
    Flags: bus master, medium devsel, latency 66, IRQ 16
    Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134



kirio.

---

### Post by razan on 2011-02-21
I managed to solve the problem. All I did was to blacklist the module tea5767 so it is not loaded at boot. I added the following line to /etc/modprobe.d/blacklist 

```
blacklist tea5767  
```

And now I can load the card and tuner of my choice. I am watching tv just fine with this tv card.

---

### Post by m0dcm on 2011-03-25
I have this TV tuner in my Sony Vaio VGC-V2M, and I cannot get it to work in Ubuntu 10.04LTS, do I do it the same way? or is there another way?

---

### Post by haintwru on 2011-03-25
I really like you

---

