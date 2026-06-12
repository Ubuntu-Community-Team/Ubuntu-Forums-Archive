---
title: "please help - No sound on IBM T41 with Ubuntu"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by redstrat on 2007-04-04
Hi,

I've installed Ubuntu onto my IBM T41 thinkpad and can't get the sound to work at all.

I've looked through the Comprehensive Sound Problem Solutions thread but that doesn't appear to have solved the problem.

I have looked at the sound settings in system and alsamixer and the PCM is not muted.

Can someone give me some guidance as to what to do next?

Thanks Matt


I get the following outputs;

--------------------

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

--------------------

lspci -v

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM: Unknown device 0537
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

--------------------

sudo modprobe snd-intel8x0

(The Konsole just takes the command and gives no response, I assume this is ok)

---

