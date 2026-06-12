---
title: "sound setup problems"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by SVWander on 2007-01-06
I am having a terrible time trying to get the sound working on my old gateway computer with a intel8x0 I am using Ubuntu 6.10. My sound was working fine and then sometime yesterday it went out. I followed the instructions in Comprehensive Sound Problem Solutions Guide v0.5e. The computer 'sees' my 

**aplay -l **

card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lspci -v **

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 2009
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at e400 [size=256]
        I/O ports at e080 [size=64]
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied> 

I have tried to: 

**Getting the ALSA drivers from a *fresh* kernel **
But it did nothing to help the situation.

I also tried:

**ALSA driver Compilation**

With the command lead to an error message both with and without choose module-assistant.

When I try the command ./configure I get this error message.

Ubuntu@tim-desktop:/usr/src$ sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=intel8x0
Password:
sudo: ./configure: command not found

What am I doing wrong? I tried the ./configure both with and without sudo.

tim](*,)

---

