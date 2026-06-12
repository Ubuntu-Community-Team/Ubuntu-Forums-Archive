---
title: "Cannot add module options for saa7134"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by hachuah on 2008-01-04
I'm quite frustrated, hopefully someone can help me out. I'm trying to add my options to the saa7134 module, but ubuntu doesn't seem to take it...

I added 
options saa7134 card=65 tuner=54 audio_ddep=4

to both the /etc/modprobe.d/options and /etc/modprobe.d/saa7134 file,
then tried rebooting and also ran update-modules.

Still, when I do, 
rmmod saa7134
modprobe saa7134

It loads the wrong tuner!!! 

[89661.169009] saa7133[0]: found at 0000:02:0d.0, rev: 208, irq: 22, latency: 64, mmio: 0xfeaff000
[89661.169017] saa7133[0]: subsystem: 1131:0000, board: V-Stream Studio TV Terminator [card=65,insmod option]
[89661.169478] saa7133[0]: board init: gpio is 40
[89661.170046] input: saa7134 IR (V-Stream Studio TV  as /class/input/input10
[89661.369727] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[89661.417606] tuner 0-004b: setting tuner address to 61
[89661.457548] tuner 0-004b: type set to tda8290+75a
[89661.569432] tuner 0-004b: setting tuner address to 61
[89661.609414] tuner 0-004b: type set to tda8290+75a
[89661.676084] saa7133[0]: Huh, no eeprom present (err=-5)?
[89664.113573] saa7133[0]: registered device video0 [v4l2]
[89664.113918] saa7133[0]: registered device vbi0
[89664.114238] saa7133[0]: registered device radio0
[89664.153534] saa7134 ALSA driver for DMA sound loaded

What can I do to get it to work??? I was using gentoo previously and never had these problems...

---

