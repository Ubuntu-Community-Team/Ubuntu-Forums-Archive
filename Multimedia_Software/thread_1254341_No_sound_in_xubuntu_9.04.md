---
title: "No sound in xubuntu 9.04"
date: 2009-08-31
forum: Multimedia Software
---

### Post by Harlequin. on 2009-08-31
Installed Xubuntu 9.04 last week after using windows all my life, getting the sound working was a bit of a headache, and after spending all week trying to get it working, I had messed it up so bad that I needed to completely reinstall Xubuntu.

So here I am, fresh from installation asking for help on how to get my sound running.  Mixer detects 3 sound cards, one is Creative SB Live, the other is some intel thing and the last is OSS.

From lspci -v:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: Intel Corporation Device 0103
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at e400 [size=256]
    I/O ports at e080 [size=64]
    Memory at febff800 (32-bit, non-prefetchable) [size=512]
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0



02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
    Subsystem: Creative Labs Device 100a
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at d880 [size=32]
    Capabilities: [dc] Power Management version 1
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1


I would like to get either of these working. I think the intel is an onboard sound card and the creative one is the one that came with my 5.1 surround sound lol.

Please keep it simple, I am very new to this lol :sad: thanks in advance.



I think the Creative card may be muted in ALSA Mixer but when I type alsamixer into terminal it automatically opens the intel one.

---

### Post by Harlequin. on 2009-08-31
Help please....

---

### Post by Harlequin. on 2009-08-31
Omg someone help please...? :confused::confused:

---

### Post by Harlequin. on 2009-08-31
Bloody hell. I JUST WANT SOUND

---

### Post by Harlequin. on 2009-08-31
...

---

### Post by Harlequin. on 2009-08-31
Found the solution, and this may be the root of most sound issues in xubuntu lol.

[B]sudo /etc/init.d/alsa-utils start

[/B]Sound worked after a reboot.

---

