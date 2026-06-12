---
title: "pvr usb2: tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)"
date: 2010-05-11
forum: Multimedia Software
---

### Post by deadland on 2010-05-11
Hi ubuntu-friends,

when I plugin my Hauppauge PVR USB2 I get the following error:

```
tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)
```

Which seems to cause problems using the IR device of the PVR.

I already tried [http://ubuntuforums.org/showthread.php?t=1475377]("My thread") to build the latest v4l-dvb and an older version, which supposed to work, but no luck.

Any ideas.

---

### Post by deadland on 2010-05-14
Bump

---

### Post by deadland on 2010-05-15
No idea?

---

### Post by deadland on 2010-05-17
I tried the Karmic Kernel (within Lucid) which workded in Karmic but this also doesn't help. So it isn't the module itselfe, it seams to be another problem, but what else could it be?

---

### Post by xc3RnbFO8P on 2010-05-17
Can you watch TV? If not show the output of:
**dmesg** and **lsusb**

---

### Post by borbasl on 2010-06-04
Hi, 

I have the same problem.

lsusb:
```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 2040:2900 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg: 
```
[  660.480214] usb 1-3: new high speed USB device using ehci_hcd and address 9
[  660.613587] usb 1-3: configuration #1 chosen from 1 choice
[  660.615917] pvrusb2: Binding ir_video to i2c address 0x18.
[  660.615986] lirc_i2c: chip 0x0 found @ 0x18 (Leadtek IR)
[  660.615994] lirc_dev: lirc_register_driver: sample_rate: 10
[  660.661594] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[  660.811629] pvrusb2: Attached sub-driver saa7115
[  660.824103] msp3400 0-0040: MSP3415G-B8 found @ 0x80 (pvrusb2_a)
[  660.824108] msp3400 0-0040: msp3400 supports nicam and radio, mode is autodetect and autoselect
[  660.824151] pvrusb2: Attached sub-driver msp3400
[  660.859214] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[  660.859228] pvrusb2: Attached sub-driver tuner
[  660.866237] tuner 0-0043: chip found @ 0x86 (pvrusb2_a)
[  660.866371] tda9887 0-0043: creating new instance
[  660.866374] tda9887 0-0043: tda988[5/6/7] found
[  660.866853] tda9887 0-0043: i2c i/o error: rc == -5 (should be 4)
[  660.866860] pvrusb2: Attached sub-driver tuner
[  660.889382] tveeprom 0-0050: Hauppauge model 29034, rev C347, serial# 6588232
[  660.889394] tveeprom 0-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
[  660.889406] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[  660.889415] tveeprom 0-0050: audio processor is MSP3415 (idx 6)
[  660.889425] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[  660.889434] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[  660.889451] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/G/H;SECAM-B/G/H
[  660.889467] pvrusb2: Mapping standards mask=0xd000f (PAL-B/B1/G/H;SECAM-B/G/H)
[  660.889476] pvrusb2: Setting up 9 unique standard(s)
[  660.889487] pvrusb2: Set up standard idx=0 name=PAL-B/G
[  660.889496] pvrusb2: Set up standard idx=1 name=SECAM-B/G
[  660.889504] pvrusb2: Set up standard idx=2 name=PAL-B
[  660.889513] pvrusb2: Set up standard idx=3 name=PAL-B1
[  660.889521] pvrusb2: Set up standard idx=4 name=PAL-G
[  660.889529] pvrusb2: Set up standard idx=5 name=PAL-H
[  660.889538] pvrusb2: Set up standard idx=6 name=SECAM-B
[  660.889546] pvrusb2: Set up standard idx=7 name=SECAM-G
[  660.889555] pvrusb2: Set up standard idx=8 name=SECAM-H
[  660.889565] pvrusb2: Initial video standard guessed as PAL-B/B1/G
[  660.889587] pvrusb2: Device initialization completed successfully.
[  660.889750] usb 1-3: firmware: requesting v4l-cx2341x-enc.fw
[  660.890792] pvrusb2: registered device video0 [mpeg]
[  660.891563] pvrusb2: registered device radio0 [mpeg]
[  661.201511] tuner-simple 0-0061: creating new instance
[  661.201517] tuner-simple 0-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[  661.326413] tda9887 0-0043: i2c i/o error: rc == -5 (should be 4)
[  661.399039] tda9887 0-0043: i2c i/o error: rc == -5 (should be 4)
[  661.402165] tda9887 0-0043: i2c i/o error: rc == -5 (should be 4)

```

---

### Post by deadland on 2010-06-07
It feels good, not to be alone with this problem :)

---

