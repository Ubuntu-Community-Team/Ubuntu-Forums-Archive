---
title: "loss of sound"
date: 2008-06-07
forum: Multimedia Software
---

### Post by roschell on 2008-06-07
can not recall the reason however couple days I found my sound had gone. running 7.04 on tecra m2 laptop. 

I followed the [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)
but with no success. 

command 'aplay -l' returns

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

command 'lspci -v' gives me

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device 0246
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at be00 [size=256]
        I/O ports at bdc0 [size=64]
        Memory at fcdffe00 (32-bit, non-prefetchable) [size=512]
        Memory at fcdffd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

thanks for help

---

