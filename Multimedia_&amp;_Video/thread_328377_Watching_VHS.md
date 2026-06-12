---
title: "Watching VHS"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2006-12-30
Hi;

About two years ago I used a knoppix linux install with kwintv and an
RFC modulator to hook up an ancient salvaged VCR directly to my
computer and watch some old VHS tapes I had.   The old VCR died.  I
have recently bought a new one and I would like to watch some VHS tapes
again on my computer.  I think I forgot some of the things I did as I
am not getting results.

Currently I have:

1. Ubuntu 6.10 ( Edgy )
2. Zapping 0.10cvs6

This HaugePauge TV card ( about 3 -4 years old ):

----------------------------------------------------------------------

TV/Radio Card ( Hauge Pauge )
lspci -vv
----------------------------------------------------------------------

02:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video 
Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- 
Stepping- SERR+ FastB2B-
	Status: Cap+ 66Mhz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- 
<TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (4000ns min, 10000ns max)
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at f47fe000 (32-bit, prefetchable) [size=4K]
	Capabilities: <available only to root>
------------------------------------------------------------------------

I am in the United States so I set the video standard as NTSC and I set
the video input as s-video.

I then turned my VCR on, set it to channel 3, put a tape in, pressed
play, and told zapping to automatically scan for channels.  If found
none.

I get nothing but a blue screen.

Any ideas what I might need to do to play the tape?

Thanks much in advance for any information

---

### Post by tinker123 on 2006-12-30
Okay, I switched from "svideo" to "television" and now it works.

However, I am having trouble with the audio.   It sounds muffled and/or screechy.  Any idea what I can do about that.

Same tapes, same hardware as two years ago, just different software, I did not have this problem.

Thanks in advance.

---

### Post by tinker123 on 2006-12-31
It is the software.   I installed kdetv and the sound was fine.   I also installed "radio" that used to come with xawtv and it sounded a lot better than the "fm tuner" gnome radio program.

---

