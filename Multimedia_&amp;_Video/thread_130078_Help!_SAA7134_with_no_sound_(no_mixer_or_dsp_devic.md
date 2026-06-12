---
title: "Help! SAA7134 with no sound (no mixer or dsp device) ..."
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by iceloki on 2006-02-15
Hi all,
    I have a SAA7134 card with a cable connected to my sound card line-in (ALSA mode). The video is played correctly and the tunner is also working correctly, but there is no sound output. The following is the dmesg output:

[4298648.638000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4298648.638000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKD] -> GSI 18 (level, low) -> IRQ 209
[4298648.638000] saa7130[0]: found at 0000:02:09.0, rev: 1, irq: 209, latency: 64, mmio: 0xff5ffc00
[4298648.638000] saa7130[0]: subsystem: 1131:2001, board: 10MOONS PCI TV CAPTURE CARD [card=21,autodetected]
[4298648.638000] saa7130[0]: board init: gpio is 19143
[4298648.745000] tuner 2-0060: All bytes are equal. It is not a TEA5767
[4298648.745000] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[4298648.745000] tuner 2-0060: type set to 37 (LG PAL (newer TAPC series))
[4298648.769000] saa7130[0]: i2c eeprom 00: 31 11 01 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[4298648.769000] saa7130[0]: i2c eeprom 10: ff ff 00 00 31 30 4d 4f 4f 4e 53 37 31 33 30 20
[4298648.769000] saa7130[0]: i2c eeprom 20: 54 04 48 53 ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.769000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.770000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.770000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.770000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.770000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4298648.783000] saa7130[0]: registered device video0 [v4l2]
[4298648.783000] saa7130[0]: registered device vbi0
[4298648.784000] saa7130[0]: registered device radio0

    From the output I think the reason is that there is no dsp0 or mixer0 device. How to enable them? I tried with modeprobe saa7134 oss=1, but there is still no the above devices, and I tried to add mixer_nr=1 and dsp_nr=1 parameters, but error shows "saa7134: Unknown parameter `dsp_nr'". Currently dsp_nr and mixer_nr is disabled? Andy then how can I specify the audio parameters?

    The lspci output is:
0000:02:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

    Anybody can give me some help on how to enable sound output.

    My system is ubuntu (depper) + Linux version 2.6.15-15-k7

    Thanks

Andy WU

---

### Post by gborzi on 2006-03-05
I have a TV card with the same chip, I suppose because lspci gives
0000:01:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
I had the some problem, and it was fixed by disabling 3D surround for line-in but I don't remember which application I used for this. Maybe kmix.

---

