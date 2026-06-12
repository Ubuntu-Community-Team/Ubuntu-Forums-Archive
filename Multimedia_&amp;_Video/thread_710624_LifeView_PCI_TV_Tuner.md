---
title: "LifeView PCI TV Tuner"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by JohnSouto on 2008-02-28
Not too long ago I installed Kubuntu on my machine and got my TV tuner working after a few google searches. I formatted my PC, installed Kubuntu again and again after a few google searches I had my tuner working. Well, foolishly, I formatted once more but this time I cannot configure my tv card properly. I've googled like no tomorrow and I cannot find that same web page I used before, this is my third or fourth day trying to get this thing to work. I'm running a LifeView PCI TV tuner (Not sure on the model, I assume it's a FlyVideo 2000). Using TVTime, I get no audio nor video from numerous configurations that I've tried. I'm quite new to Linux to be honest, so I don't know what else I could say that would be helpful. Here is an lspci and lspci -n dump:

[http://members.byond.com/Crashed/files/lspci-output.txt](http://members.byond.com/Crashed/files/lspci-output.txt)
[http://members.byond.com/Crashed/files/lspciN-output.txt](http://members.byond.com/Crashed/files/lspciN-output.txt)

---

### Post by JohnSouto on 2008-02-29
I've figured out that my card is most likely a #3, a FlyVideo 3000 or more likely #2 FlyVideo 2000. And the tuner is either 15 or 2 - NTSC. I've been stuck on this problem for a few days now, but I'm positive I can get this working because I've had it working before. Here's output from dmesg after I rmmod'd the saa7134 modules, then I tried modprobe saa7134 card=2 tuner=15. 

[17180059.288000] saa7134 ALSA driver for DMA sound unloaded
[17180074.844000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17180074.848000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 58
[17180074.848000] saa7130[0]: found at 0000:05:06.0, rev: 1, irq: 58, latency: 32, mmio: 0xd2000000
[17180074.848000] saa7130[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[17180074.848000] saa7130[0]: board init: gpio is 38500
[17180074.848000] saa7130[0]: there are different flyvideo cards with different tuners
[17180074.848000] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[17180074.848000] saa7130[0]: option to override the default value.
[17180074.968000] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input4
[17180075.168000] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[17180075.172000] tuner 2-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17180075.180000] tuner 2-0063: chip found @ 0xc6 (saa7130[0])
[17180075.184000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17180075.220000] saa7130[0]: registered device video0 [v4l2]
[17180075.220000] saa7130[0]: registered device vbi0
[17180075.224000] saa7130[0]: registered device radio0
[17180075.244000] saa7134 ALSA driver for DMA sound loaded
[17180075.244000] saa7130[0]/alsa: saa7130[0] at 0xd2000000 irq 58 registered as card -1

---

