---
title: "Nova HD S2 Card Installation"
date: 2012-01-16
forum: Mythbuntu
---

### Post by jimyhunt on 2012-01-16
Hello, I have bought a Nova HD S2 card. I have a question regarding installation.

Should it appear as in /dev/dvb ?

Its being registered as /dev/video0. 

```
 dmesg | grep -i cx
[   20.137628] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   20.137686] cx8800 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   20.142453] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   20.142567] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   20.142573] cx88[0]: TV tuner type -1, Radio tuner type -1
[   20.577427] tveeprom 0-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   20.577440] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[   20.577448] cx88[0]: hauppauge eeprom: model=69100
[   20.734052] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:02:0b.0/rc/rc0/input4
[   20.734578] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:02:0b.0/rc/rc0
[   20.898262] cx88[0]/0: found at 0000:02:0b.0, rev: 5, irq: 23, latency: 64, mmio: 0xf3000000
[   20.913561] cx88[0]/0: registered device video0 [v4l2]
[   20.913827] cx88[0]/0: registered device vbi0
[   20.914011] cx88[0]/2: cx2388x 8802 Driver Manager
[   20.914034] cx88-mpeg driver manager 0000:02:0b.2: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   20.914046] cx88[0]/2: found at 0000:02:0b.2, rev: 5, irq: 23, latency: 64, mmio: 0xf5000000
[   20.941184] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   20.941192] cx88/2: registering cx8802 driver, type: dvb access: shared
[   20.941199] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   20.941206] cx88[0]/2: cx2388x based DVB/ATSC card
[   20.941211] cx8802_alloc_frontends() allocating 1 frontend(s)
[   20.961994] cx2388x alsa driver version 0.0.8 loaded
[   20.962098] cx88_audio 0000:02:0b.1: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   20.962156] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   20.968706] cx24116_readreg: reg=0xff (error=-6)
[   20.969483] cx24116_readreg: reg=0xfe (error=-6)
[   20.969489] Invalid probe, probably not a CX24116 device
[   20.969507] cx88[0]/2: frontend initialization failed
[   20.969513] cx88[0]/2: dvb_register failed (err = -22)
[   20.969518] cx88[0]/2: cx8802 probe failed, err = -22
[   20.975100] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0

```


The guide states it should appear in DVB DTV capture card (v3.x) but it doesn't

What is missing?

---

### Post by langner on 2012-01-18
HI,

Have you checked the backend in the capture cards section and changed it to 'DTV capture card (v3.x)', as it may still work.

Matt

---

### Post by nickrout on 2012-01-18
> **jimyhunt said:**
> Hello, I have bought a Nova HD S2 card. I have a question regarding installation.

Should it appear as in /dev/dvb ?

Its being registered as /dev/video0. 



says who? i don't see where it says that in your quoted dmesg

---

### Post by jimyhunt on 2012-01-20
It doesn't appear in the mythtv setup. All cards taken.

I tried removing the other freview cards, but still the same problem.

The log indicates this:

[   20.913561] cx88[0]/0: registered device video0 [v4l2] [   20.913827] cx88[0]/0: registered device vbi0

---

### Post by nickrout on 2012-01-20
Sorry dunno how I missed that line.

any dvb device should appear as /dev/dvb/adapterX where X starts at 0 for the first card and increases for each tuner.

So when you go into mythtv setup, add a tuner and change the type to dvb, it says there are no cards available?

Has the firmware loaded? I can't see mention of it in the dmesg log (again I might be blind, but you have filtered it through 'grep cx88' so it may indeed be loaded).

---

