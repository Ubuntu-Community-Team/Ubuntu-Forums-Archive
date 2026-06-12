---
title: "MSI TV @nywhere"
date: 2009-02-25
forum: Multimedia Software
---

### Post by Azr@el on 2009-02-25
Hi Forum,

i am pretty new to TV on linux and i'm kinda stuck. I have a MSI TV @nywhere Pro PCI and I am trying to get television working.
I tested xawtv and tvtime and neither is able to find any channels, i guess it's because they can't open the card's tuner. Does anyone know which tuner this card is using? Or am i just doing anything totally wrong?

I hope anyone can give me some directions.

Regards, Azr@el


Here are some dumps:

lspci -vnn
```

02:08.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Device [1462:8803]
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ea000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: saa7134
        Kernel modules: saa7134

```

xawtv -hwscan
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-11-generic)
looking for available devices
port 57-57
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

port 58-73
    type : Xvideo, image scaler
    name : Radeon Textured Video

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UNKNOWN/GENERIC
    flags: overlay capture

```

```
[   15.416302] saa7134 0000:02:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   15.416308] saa7134[0]: found at 0000:02:08.0, rev: 1, irq: 16, latency: 32, mmio: 0xea000000
[   15.416314] saa7134[0]: subsystem: 1462:8803, board: UNKNOWN/GENERIC [card=0,insmod option]
[   15.416323] saa7134[0]: board init: gpio is c0407f
[   15.568038] saa7134[0]: i2c eeprom 00: 62 14 03 88 10 28 ff ff ff ff ff ff ff ff ff ff
[   15.568047] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568055] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568062] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568069] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568076] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568083] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568090] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568097] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568104] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568111] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568118] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568125] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568132] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568139] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.568146] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.570571] saa7134[0]: registered device video0 [v4l2]
[   15.570622] saa7134[0]: registered device vbi0
[   15.590961] saa7134 ALSA driver for DMA sound loaded
[   15.590989] saa7134[0]/alsa: saa7134[0] at 0xea000000 irq 16 registered as card -2

```

---

### Post by jmengle on 2009-02-25
Ive got one of those cards, mine uses a Microtuner MT2032, but yours may be different. I also had to unsolder the metal shield above the tuner chip to visually see what number it was, the tuner chip is the one closest to the coax cable connector and it has  (usually) a metal shield covering it up.

Other common tuner types for MSI cards are some kind of Phillips tuner.
I guess you just have to look. I can't find any command that lists the type of tuner, only the chipset id'd by lspci

Jim

---

### Post by Maheriano on 2009-02-25
In for a fix. I have the same card.

---

### Post by Azr@el on 2009-02-25
Hi

Thanks for your response, though i'm not likely to fumble that shield off, for it's my girlfriend's card and she furiously protects her hardware from me :(
Any non-electronical hints?

Regards, Azr@el

PS: Are we sure that the missing tuner info is causing this issue?

---

### Post by Azr@el on 2009-03-01
Hi

So, i managed to get my hands on that metal shield. Turns out that i have number 61 from the CARDLIST.tuner: TNF 9533

I am wondering how to proceed, still i don't get any channels in kdetv, tvtime does not "find any tuner on input 61". Any hints or papers to point me into the right direction?

Regards, Azr@el

---

