---
title: "Does Xubuntu Have Sound?"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Jack Jebedee on 2006-06-08
jebedee@Guest:~$ sudo modprobe snd-sb16
FATAL: Error inserting snd_sb16 (/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb16.ko): No such device

jebedee@Guest:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
lawrence@Guest:~$

[COLOR="Blue"]Hmmm...  I don't have a Soundblaster 16 driver in Xubuntu (or the directory it's supposed to be in, for that matter).  And I don't have Alsamixer to see if the driver is already loaded but the sound is turned down.  I know that Xubuntu is reported to be a faster, leaner version of Ubuntu.  Was sound one of the features that was sacrificed for speed?

... JJ[/COLOR]

---

### Post by ranf on 2006-06-09
Is that an ISA card?

---

### Post by Jack Jebedee on 2006-06-18
Yes, it's an ISA Creative Labs Soundblaster 16.  Works perfectly with ancient Windows ME (no longer supported by Microsoft, which is just as well).

I thought that it might have something to do with me installing Xubuntu rather than the full-bore Ubuntu, so I overwrote it with Ubuntu, but the same problem exists with Ubuntu, too.  (Say that three times fast.)

Processor is Pentium MMX 233 Mhz, RAM = 256 Mb (max load for that motherboard) with 10 Gb boot drive, dual-boot with WinME.

I'm running full Ubuntu on a second computer, Pentium III at 533 Mhz, 768 Mb RAM and 30 Gb boot drive, also dual-boot with WinME.  Correction:  I ***WAS*** running it until this morning.  Now it tells me after the POST:  "Insert system disk and press <Enter> to continue..."  Aarrgghh!  I hate it when that happens.  (Fortunately, this is the first time it's happened.)  I don't know if GRUB had anything to do with the problem.  The first thing I'll try is a boot from the WinME Emergency floppy disk (What the heck is a *floppy* disk, for crying out loud?) and SYS C: it back to life.  If that doesn't work, I'll have to be a little more creative.

... JJ

---

### Post by ranf on 2006-06-18
[QUOTE=Jack Jebedee]Yes, it's an ISA Creative Labs Soundblaster 16.  Works perfectly with ancient Windows ME (no longer supported by Microsoft, which is just as well).
[/QUOTE]
ISA cards are complicated (by design).
First grab as much info as you can get from Windows device manager. Stuff like IRQ, ioport, DMA addresses.

The linux kernel module can be loaded with additional parameters. To find their names and parameter types use this:
```
modinfo snd-sb16
```
IIRC the "port" parameter might just be enough.

[QUOTE=Jack Jebedee]
I thought that it might have something to do with me installing Xubuntu rather than the full-bore Ubuntu, so I overwrote it with Ubuntu, but the same problem exists with Ubuntu, too.  (Say that three times fast.)
[/QUOTE]
Ubuntu and Xubuntu use the same kernel.

---

