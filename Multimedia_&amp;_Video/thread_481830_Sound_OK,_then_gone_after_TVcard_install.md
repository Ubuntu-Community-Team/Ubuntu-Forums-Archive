---
title: "Sound OK, then gone after TVcard install"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by jharadie on 2007-06-22
I admit it: I'm still lost too often.

Using Feisty 7.04 fully updated.  Box has built-in SiS SI7012 soundcard, which worked fine via alsa until I installed a TV tuner card.  Dmesg info:

[  148.095276] bttv: driver version 0.9.16 loaded
[  148.095285] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  148.095389] bttv: Bt8xx card found (0).
[  148.095435] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 20
[  148.095452] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 20, latency: 32, mmio: 0xcfcfe000
[  148.095466] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[  148.095514] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[  148.097074] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[  148.097080] bttv0: using tuner=-1
[  148.097085] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  148.097810] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  148.098524] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  148.099238] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  148.100000] bttv0: registered device video0
[  148.100044] bttv0: registered device vbi0
[  148.119582] bt878: AUDIO driver version 0.0.0 loaded
[  148.119655] bt878: Bt878 AUDIO function found (0).
[  148.119686] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 20
[  148.119696] bt878_probe: card id=[0x0],[ <NULL> ] has DVB functions.
[  148.119707] bt878(0): Bt878 (rev 17) at 00:09.1, irq: 20, latency: 32, memory: 0xcfcff000

A connection wire came with the TV card, I'm guessing to go from Audio Out to soundcard Line In.  No luck.  Also, on boot, machine says TVcard is IRQ 5, same as one of the USB ports.

Before I try using the TVcard, I'd like to get my sound back.   When I go to Sound Preferences, under Devices, I can successfully test the SiS, but when I try alsa it says:

audiotestsrc wave=sine freq=512 !
audioconvert ! audio resample ! gconfaudiosink:
Could not open resource for writing.

Doing sudo locate gconfaudiosink returns nothing.  Also, doing alsamixer or sudo alsamixer says "no mixer elems found."

All suggestions appreciated.  Thanks.

Update: doing sudo modprobe -v -r bttv results: FATAL: Module bttv is in use.

---

