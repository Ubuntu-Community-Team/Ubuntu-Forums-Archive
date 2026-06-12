---
title: "Volume increments are way wrong"
date: 2009-11-04
forum: Multimedia Software
---

### Post by Vostrocity on 2009-11-04
I finally upgraded to Karmic. Well a few things changed about my sound settings. First, mute works properly without static sounds. Second, the panel icon and my keyboard hotkey now control the same setting, whereas they were separate volume settings before. Third, **volume increments are way wrong**. The sound is completely gone at 3 steps before the lowest point, while the sound is unbearably loud before I even get halfway on the volume bar. That means I only get about 4 increments. Anyone have a solution?

---

### Post by Kushkah on 2009-11-04
Sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420578"), check out [http://ubuntuforums.org/showthread.php?t=1309427](http://ubuntuforums.org/showthread.php?t=1309427) and see if that works for you. :)

---

### Post by abobo123 on 2009-11-05
I have the same problem.  I just upgraded to 9.10.  Before, i could open the large volume panel and turn one of the sliders (i think it said PCM) down so it didn't blow my speakers/headphones out and i could use the main volume control just fine.  The new panel only has one thing for vol. control, and at 10% it's overdriving my laptop speakers.  Also, without being on mute the speakers constantly hiss.  I'm using a toshiba U205 series laptop.  Anyone else experience this?  Anyone know of a fix?

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:0001]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 44080000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by abobo123 on 2009-11-05
I jumped the gun, solution in the post above.  Thanks Kushkah

---

### Post by Vostrocity on 2009-11-07
Sorry for the late reply but thanks that worked.

---

