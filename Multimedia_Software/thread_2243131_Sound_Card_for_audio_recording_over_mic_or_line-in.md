---
title: "Sound Card for audio recording over mic or line-in"
date: 2014-09-06
forum: Multimedia Software
---

### Post by MakOwner on 2014-09-06
I know this is really broad and probably tired question, but I can't seem to find a really good answer anywhere other than "it depends".

Here's what I want to do, and I need a sound card that can excel at this - anyone here have suggestions?

I want to record an FM and HDFM signal off the air and record it at the highest fidelity I can reasonably achieve.

This is the hardware I currently have - System 1:
Dell PowerEdge 850 server 64bit 3.2.0-68 kernel on a 12.0.4.5 LTS server install (CLI only) 
Insignia Desktop AM/FM/HDFM reciever
Connected via stereo 3.5mm jack line from the headphone out to the mic/line-in jack on this sound card
ASUX Xonar DSX PCIe 7.1 Sound card
(asreported by lspci)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 8522
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ec00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: snd_virtuoso
	Kernel modules: snd-virtuoso



System 2:
Dell PowerEdge 850 server 64bit 3.13.0-35 kernel on a 12.0.4.5 LTS server install (CLI only) 
Rolls HR78 AM/FM PLL tuner
Connected by 3.5mm stereo jack line from a L/R RCA adapter to 3.5mm jack to the mic/line-in jack on this card:
ASUS Xonar DX PCIE 7.1 sound card
(As reported by lspci)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 8522
	Flags: bus master, medium devsel, latency 32, IRQ 16
	 I/O ports at ec00 [size=256]
	 Capabilities: [c0] Power Management version 2
	Kernel driver in use: snd_virtuoso
	Kernel modules: snd-virtuoso



Although these report the same to the OS (drivers are the same I suspect) they are slightly different models of the Xonar HD sound card. 
The differences between the kernels has something to HWE.

Recording levels are set for the mic input of the soundcards using alsamixer on each system.
(I have tried the line-in input on both systems and the output is so muted as to be useless - or I don't know how to properly process it afterwards.)

My current issue is that I get really nice stereo separation on the Rolls FM recorder, but I wond up with some really nasty hissing on the high end and I have some issues with clipping on playback on _some_ equipment.
The Insignia desktop produces excellent sound when played though locally attached headphones, but when playing back the recording I get 98% of the sound in one channel and quite frequently a really strange echo/warble.

I suspect an issue with the Xonar sound card and possibly some driver in this instance because when I first started recording from this source, it had excellent sound and separation.


All of this is done strictly via scripts from the CLI so I can use cron to launch the jobs at appropriate times.

I use arecord to capture to .wav format Signed 16 bit Little Endian, Rate 48000 Hz, Stereo on both systems.
I use sox to combine the out of arecord into a single file when it exceeds the single file recording limit.
I use lame to convert to mp3 for playback, primarily from an old ipod that gets connected to a couple of different car stereos (where the hissing and clipping are the most obvious) - playback from the cheap speakers and what not in my laptop pretty much mask all the crud in the recording.  

The content that I'm recording is a talk show that is interspersed with what North Americans seem to think is music.  Some of it won't won't make your ears bleed. The host frequently makes use of the stereo separation in the humorous "bits" they have, thus my desire to record in quality stereo rather than just voice quality/level.

As I said, at present I suspect an issue with the sound card when recording from the HDFM source.  
I'm looking for a sound card that will provide the quality with ease of installation - Just works after a server install and and alsa/sox/arecord/lame like these do - sort of.


So, short version of the question - I'm looking for the best hardware to make this happen.
Please make suggestions?

---

