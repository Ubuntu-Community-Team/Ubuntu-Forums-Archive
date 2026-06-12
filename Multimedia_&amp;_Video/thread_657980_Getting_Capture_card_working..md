---
title: "Getting Capture card working."
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by ingaz on 2008-01-04
Hi;

I have a KGuard Security capture card, based on the saa7134.

I have it happily working, but am unable to change inputs. From various messages it would appear that ubuntu (7.10) is not picking up the various inputs.

ie, excerpt from dmesg:

```
[   53.523951] Linux video capture interface: v2.00
[   53.792820] saa7130/34: v4l2 driver version 0.2.14 loaded
[   53.793051] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   53.793085] saa7134[0]: found at 0000:01:0b.0, rev: 1, irq: 9, latency: 64, mmio: 0xff8ffc00
[   53.793107] saa7134[0]: subsystem: 17de:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   53.793154] saa7134[0]: board init: gpio is e0d0000
[   54.040646] saa7134[0]: i2c eeprom 00: de 17 00 00 10 a0 ff ff ff ff ff ff ff ff ff ff
[   54.040687] saa7134[0]: i2c eeprom 10: 24 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040723] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040758] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040793] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040828] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040864] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.040899] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   54.041228] saa7134[0]: registered device video0 [v4l2]
[   54.041311] saa7134[0]: registered device vbi0

```

and the inputs section from v4l-info

```
inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "default"
        type                    : CAMERA
        audioset                : 1
        tuner                   : 0
        std                     : 0xffbdff [PAL_B,PAL_B1,PAL_G,PAL_H,PAL_I,PAL_D,PAL_D1,PAL_K,PAL_M,PAL_Nc,PAL_60,NTSC_M,NTSC_M_JP,?,SECAM_B,SECAM_D,SECAM_G,S
ECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB]
        status                  : 0x0 []

```

does anyone have any ideas?

---

### Post by ingaz on 2008-01-06
hmmm...

prod

---

### Post by tmcguire on 2008-06-25
I am trying to get ZoneMinder Working with Xubuntu 8.04. I installed from Synaptic. How can I check to see if my KGUARD 8 Port Digital Security System Model TV-KW-SEC800A is working? A review at Newegg [http://www.newegg.com/Product/Product.aspx?Item=N82E16815100122](http://www.newegg.com/Product/Product.aspx?Item=N82E16815100122) said that it works under Linux. Is there a hardware manager in Xubuntu? I have tried using Camorama, but it shows only lines. Not sure if it is what my camera is on or not. Thanks in advance for any guidance!

---

