---
title: "Dead PVR-150???"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by bblank27 on 2007-12-08
I am coming up with what looks like a bad tuner card.  It is showing no eeprom...  Am I correct in this conclusion?

When use:
dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac

I get the following:
[   28.024193] ivtv:  ==================== START INIT IVTV ====================
[   28.024199] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   28.024335] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   28.024395] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 21
[   28.167649] input: ImPS/2 Generic Wheel Mouse as /class/input/input4
[   28.171010] parport_pc 00:06: reported by Plug and Play ACPI
[   28.171118] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   28.705524] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3754608392 bytes)
[   28.918231] ivtv0: Encoder revision: 0x02050032
[   28.918236] ivtv0: Recommended firmware version is 0x02060039.
[   28.929845] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   28.929851] tveeprom 0-0050: Encountered bad packet header [00]. Corrupt or not a Hauppauge eeprom.
[   28.929855] ivtv0: Invalid EEPROM
[   28.957908] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   28.990377] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.003009] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   29.004047] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.008256] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.009315] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.010216] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.010905] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.010933] wm8775 0-001b: I2C: cannot write 021 to register R11
[   29.012067] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.014209] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.014237] wm8775 0-001b: I2C: cannot write 102 to register R12
[   29.015259] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.017052] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.017978] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.018402] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.018430] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   29.019018] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.019907] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.020330] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.020358] wm8775 0-001b: I2C: cannot write 1bf to register R16
[   29.020995] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.022113] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.022795] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.022822] wm8775 0-001b: I2C: cannot write 185 to register R17
[   29.023221] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.023890] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.024882] wm8775 0-001b: I2C: cannot write 0a2 to register R18
[   29.025279] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.025706] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.026129] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.026157] wm8775 0-001b: I2C: cannot write 005 to register R19
[   29.026800] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.027669] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.028336] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.028363] wm8775 0-001b: I2C: cannot write 07a to register R20
[   29.028961] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.030336] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   29.030342] ivtv0: i2c addr 0x44 not found for command 0x4008646f!
[   29.031233] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.033477] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.035270] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.035700] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.036307] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.036336] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   29.036991] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.037895] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.039003] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.039031] wm8775 0-001b: I2C: cannot write 102 to register R21
[   29.039033] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0x4008646d!
[   29.145751] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   29.145757] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   29.145763] tuner 0-0061: tuner type not set
[   29.147137] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.148133] wm8775 0-001b: I2C: cannot write 0c0 to register R21
[   29.148791] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.150143] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.150574] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.150601] wm8775 0-001b: I2C: cannot write 1d4 to register R14
[   29.151249] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.151872] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.152289] i2c-adapter i2c-0: sendbytes: error - bailout.
[   29.152316] wm8775 0-001b: I2C: cannot write 1d4 to register R15
[   29.257521] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[   29.257636] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   29.257833] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   29.258031] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   29.258133] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   29.258341] ivtv0: Registered device radio0 for encoder radio
[   29.258354] tuner 0-0061: tuner type not set
[   29.258371] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   29.258401] ivtv:  ====================  END INIT IVTV  ====================

---

