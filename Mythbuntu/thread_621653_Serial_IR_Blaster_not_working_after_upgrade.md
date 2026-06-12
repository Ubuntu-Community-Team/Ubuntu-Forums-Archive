---
title: "Serial IR Blaster not working after upgrade"
date: 2007-11-23
forum: Mythbuntu
---

### Post by SyvanX on 2007-11-23
I upgraded my MythTV box from Feisty to Gutsy this morning.  Everything seems in working order - except my IR Blaster.  

The first thing I did on upgrade was to follow the guides to recompile the lirc-modules-source to get the transmitter working again.  When I attempt a channel change, the transmitter's red LED blinks successfully, but it does not change the channel on the cable box.  

I've purged, then reinstalled lirc, I've recompiled the lirc-modules-source over and over again, I really don't know where to go from here.  Any help is greatly appreciated.

I've even reverted to the IR Blaster as my only lirc device, and it still won't successfully change channels.  It doesn't give me any error messages when using irsend.

dmesg output:
```
~$ dmesg | grep lirc
[   84.108248] lirc_dev: IR Remote Control driver registered, at major 61 
[   84.648469] lirc_serial: auto-detected active high receiver
[   84.648478] lirc_dev: lirc_register_plugin: sample_rate: 0
:~$ dmesg | grep serial
[   33.353390] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   50.549652] tveeprom 1-0050: Hauppauge model 48132, rev K268, serial# 8512193
[   84.648469] lirc_serial: auto-detected active high receiver

```

```
~$ uname -r
2.6.22-14-generic

```

---

### Post by abarbaccia on 2007-12-28
I am not using mythbuntu but am having the exact same problem. The device will blink as if it were transmitting but the channels will not change. I am working on downgrading to feisty source packages to see if the error resides there or with gutsy.

---

