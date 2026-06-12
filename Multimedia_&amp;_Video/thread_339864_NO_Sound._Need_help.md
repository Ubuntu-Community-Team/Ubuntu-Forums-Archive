---
title: "NO Sound. Need help"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by desper on 2007-01-16
[COLOR="Red"]Solved. Thanx Guy. Alsamixer unchecked all the option in last tab...then it is OK[/COLOR]

Hello, Thanx in advance

I cannot hear any sound and unfortunately i am not deaf.
It seems ubuntu-dapper (kernel 2.6.15-27-386)
recognised my sound chip..and all the options in alsamixer is unmuted.
just no sound. no beep, no start up sound. it is somewhat funny i can see the visual effct in Totem but no sound heard, when playing an ogg file.

I tried this in my shell
==================================
angela@angela-laptop:~$ sudo lspci -v

====here comes the relevant output==========

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Sony Corporation: Unknown device 81c0
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
=================================

Any known solution?I am a real newbie

---

### Post by Sqwishy on 2007-01-16
did you install alsa?

---

