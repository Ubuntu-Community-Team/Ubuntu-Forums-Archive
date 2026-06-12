---
title: "[SOLVED] CA0106 Creative SoundBlaster Audigy SE Strange Input Issues"
date: 2008-10-29
forum: Multimedia Software
---

### Post by jimmio on 2008-10-29
Hello all,
The sound works beautifully, but, the input is distorted. This distortion disappears when I start jack and Ardour, I haven't been able to find a reason so far... It's so strange... It's preventing me from using my PC as an amp for vocals/guitar... anyone know of a fix? I was thinking it might be the frequency that's the issue... setting this card to 44100 causes Windows to blue screen, it needs 48000 or 96000 supposedly...

---

### Post by markbuntu on 2008-10-29
Audigy cards only work on 48000. You need to setup both jack and ardour to 48000 for them to work properly. 44100 is not an option with that card.

---

### Post by jimmio on 2008-10-29
I wasn't asking about Jack or Ardour.... I get distortion when NOT using them... anyone know why?

---

### Post by jimmio on 2008-10-30
Not exactly sure how to get the current bitrate of the device... but lspci -vvv shows:
```
04:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Unknown device 100a
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at dce0 [size=32]
	Capabilities: <access denied>
```

Issue is still present... this isn't really even distortion... it's like... "digitization"... as if the sound isn't too loud, just poor quality.

---

### Post by markbuntu on 2008-10-30
Ok, sorry, I must have misread your post. There are a few things you can check. First of all, when not using jack have you tried turning the capture levels down in the volume control. If that does not help, try editing /etc/pulse/daemon.conf. Look for the line 

;default-sample-rate = 44100

change it to

default-sample-rate = 48000

You can also try changing the lines

;default-fragments = 4
;default-fragment-size-msec = 25

to

default-fragments = 8
default-fragment-size-msec = 5

Try the default sample rate thing first. If it doesn't work or makes things worse, you can easily put it back the way it was. Same with the defalt fragment lines.

---

### Post by jimmio on 2008-10-30
Thank you!! I skipped 48000 and went right to 96000, then went and turned all sound over to PulseAudio... works PERFECT! Thanks!

---

