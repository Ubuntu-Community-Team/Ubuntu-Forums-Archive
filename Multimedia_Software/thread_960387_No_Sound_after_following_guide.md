---
title: "No Sound after following guide"
date: 2008-10-27
forum: Multimedia Software
---

### Post by hatstand on 2008-10-27
HI all.

I am very frustrated indeed. Just got issued a new work computer and installed 8.04 on it. No sound! Upgraded to 8.10 and still no sound!

Have tried this

[Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")

and this

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Which means that I have recompiled ALSA from source. Done this 4 timesnow, using different modules and snd commands.

cat /proc/asound/card0/codec#* | grep Codec
gives
RealTekALC660

asoundconf list
gives
Intel

lspci -v
gives
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 1263
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


And still no sound. Have tried booting XP, muting volume, booting ubuntu, booting xp and unmuting volume, rebooting ubuntu. No sound. Not from speakers, nor from headphones.

Help much appreciated guys and gals!

---

### Post by markbuntu on 2008-10-28
There are quite a few options for that sound chip, all you can do is try them until you find the one that works for you:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

There is also some very basic sound setup troubleshooting at the beginning of this guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by hatstand on 2008-11-11
Well, something worked. It was either on of the first two links there, or the new upgrade. I did them all (long and dull process!) and then restarted. et viola!

Thanks for replying, markbuntu

---

