---
title: "No Sound. Howto restore default sound driver/settings"
date: 2010-06-10
forum: Multimedia Software
---

### Post by lindude on 2010-06-10
Hi, I have no sound, is it possible to restore the default sound drivers/settings in 10.04?

It was work well before except for one issue, I couldn't get mic in for Rosetta Stone using wine. 
I have followed so many howto's to try and get Rosetta Stone working and then my sound working again.
I think this is my main problem I upgraded alsa to "alsa-driver-1.0.23". I could easily be wrong about that assumption though.

I have a Dell XPS M1210
Ubuntu 10.04 64bit

I think this is my sound card, "lspci -v | less"

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01d7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel


But I don't think it is being recognized,
$ aplay -l
aplay: device_list:223: no soundcards found...

$ arecord -l
arecord: device_list:223: no soundcards found...

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 31 2010 for kernel 2.6.32-22-generic (SMP).


Do I need to do something to the Alsa settings?

I also had a Dell tech around today and he installed new speaker and they work fine.
I've tried a live cd of 10.04 and the sound works.

I hope my questions aren't to varied.
Thanks for any help!

---

### Post by lindude on 2010-06-10
Sorted, I reinstalled the alsa-driver-1.0.23 and it is working this time.
Maybe it didn't work properly the first time because when I installed it my speaker were working properly.
Can this post be removed?
Thanks

---

