---
title: "snd-bt87x"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by dshepard on 2006-06-07
I have a TV Wonder Pro card and I can't get snd-bt87x to create /dev/dsp? even though it loads. I had this card working with btaudio just fine in FC2 before switching over to Ubuntu 6. I also have a SB Live that is working fine.

I have tried blacklisting bttv, and bt878 to no avail.

If I load snd-bt87x and then load bt878 I get this in dmesg:

[4369904.987000] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 18 (level, low) -> IRQ 169
[4369904.987000] bttv0: Bt878 (rev 2) at 0000:01:04.0, irq: 169, latency: 32, mmio: 0xdeafe000
[4369904.987000] bttv0: detected: ATI TV Wonder [card=63], PCI subsystem ID is 1002:0001
[4369904.987000] bttv0: using: ATI TV-Wonder [card=63,autodetected]
[4369904.987000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4369905.139000] msp3400 0-0040: chip=MSP3445G-B8 +nicam +simple +simpler +radio mode=simpler
[4369905.140000] msp3400 0-0040: msp34xxg daemon started
[4369905.205000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[4369905.205000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[4369905.247000] bttv0: using tuner=19
[4369905.247000] tuner 0-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[4369905.247000] bttv0: i2c: checking for MSP34xx @ 0x80... found
[4369905.258000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4369905.260000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4369905.262000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4369905.274000] bttv0: registered device video0
[4369905.275000] bttv0: registered device vbi0
[4369905.322000] bttv0: PLL: 28636363 => 35468950 .. ok
[4369905.444000] bt878: AUDIO driver version 0.0.0 loaded
[4369905.445000] bt878: Bt878 AUDIO function found (0).
[4369905.445000] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 18 (level, low) -> IRQ 169
[4369905.445000] bt878(0): Bt878 (rev 2) at 01:04.1, irq: 169, latency: 32, memory: 0xdeaff000
[4370135.736000] bt878(0): unloading
[4370135.736000] bt878_mem: 0xf8ad6000.
[4370135.736000] ACPI: PCI interrupt for device 0000:01:04.1 disabled
[4370155.311000] bt878: AUDIO driver version 0.0.0 loaded
[4370155.311000] bt878: Bt878 AUDIO function found (0).
[4370155.311000] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 18 (level, low) -> IRQ 169
[4370155.311000] bt878(0): Bt878 (rev 2) at 01:04.1, irq: 169, latency: 32, memory: 0xdeaff000


---------------------------------------

If anyone can help me I would greatly appreciate it.

dan

---

### Post by tjroth on 2006-09-21
bt878: AUDIO driver version 0.0.0 loaded

The part I don't get is that.  I'm getting very poor audio capture quality (probably audio card driver).  So I'm really interested in getting btaudio working.  Mine shows the version as 0.0.0 as well.

-- TJ

---

### Post by tbonius on 2006-09-26
I was under the impression that bt878 is no longer needed.  snd_bt87x creates ALSA HW device IDS (cat /proc/asound/cards).. and if alsa-oss is installed then you also get /dev/adspX for the extra OSS device ID.  Anyone else have any input on this?

T

---

