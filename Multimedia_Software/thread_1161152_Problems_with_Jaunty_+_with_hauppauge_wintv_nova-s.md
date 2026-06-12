---
title: "Problems with Jaunty + with hauppauge wintv nova-s plus pci"
date: 2009-05-16
forum: Multimedia Software
---

### Post by Uter on 2009-05-16
Hi @ all

I am new at this forum but I am using Ubuntu since several years. In the past I never had big troubles with my tv-card, but now I have a new system and wanted to use the new Ubuntu distribution (Jaunty). 

I get this output of the logs:

dmesg

```

[ 1094.171441] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[ 1094.172524] cx88[0]: subsystem: ffff:ffff, board: Hauppauge Nova-S-Plus DVB-S [card=37,insmod option], frontend(s): 1
[ 1094.172528] cx88[0]: TV tuner type 4, Radio tuner type -1
[ 1094.292614] tveeprom 3-0050: Huh, no eeprom present (err=-6)?
[ 1094.292619] tveeprom 3-0050: Encountered bad packet header [00]. Corrupt or not a Hauppauge eeprom.
[ 1094.292623] cx88[0]: warning: unknown hauppauge model #0
[ 1094.292625] cx88[0]: hauppauge eeprom: model=0
[ 1094.292710] input: cx88 IR (Hauppauge Nova-S-Plus  as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/input/input7
[ 1094.324110] cx88[0]/2: cx2388x 8802 Driver Manager
[ 1094.324133] cx88-mpeg driver manager 0000:05:01.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1094.324146] cx88[0]/2: found at 0000:05:01.2, rev: 5, irq: 17, latency: 64, mmio: 0xfc000000
[ 1094.335131] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[ 1094.335137] cx88/2: registering cx8802 driver, type: dvb access: shared
[ 1094.335142] cx88[0]/2: subsystem: ffff:ffff, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[ 1094.335146] cx88[0]/2: cx2388x based DVB/ATSC card
[ 1094.335148] cx8802_alloc_frontends() allocating 1 frontend(s)
[ 1094.375476] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-6)
[ 1094.375482] CX24123: wrong demod revision: fa
[ 1094.375570] cx88[0]/2: frontend initialization failed
[ 1094.375574] cx88[0]/2: dvb_register failed (err = -22)
[ 1094.375578] cx88[0]/2: cx8802 probe failed, err = -22

```When I am adding the cx88-dvb module - I will get this:

```

FATAL: Error inserting cx88_dvb (/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```I cant create "/dev/dvb/" ....

I can add cx88-dvb when I am deleting all files in (/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/cx88 and compile the v4l drivers - but then I can't using scan....


Have someone experience with my Tv-Card and will be so nice to helps me ? 

Sorry for my bad english, it isn't my native language *G* 

Ps: I am using ubuntu 64bit jaunty

cheers,
Uter

---

### Post by Uter on 2009-05-18
*push*

---

### Post by Uter on 2009-05-21
*again*

---

### Post by xc3RnbFO8P on 2009-05-21
Did you ever try **sudo modprobe cx88-dvb**

---

### Post by Uter on 2009-05-24
sure !!!!

---

