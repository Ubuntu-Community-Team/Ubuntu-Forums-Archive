---
title: "curious sound recording problem - static, snap, crackle, pop"
date: 2009-01-09
forum: Multimedia Software
---

### Post by relic70 on 2009-01-09
The Rice Crispies sounds are the only sounds I could think of to describe the popping, crackling, popping, or static I hear in the background of the recorded audio when I record audio through Gnome Sound Recorder or Audacity.

I recently installed Intrepid and configured the Pulse Audio as per 

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

and

[http:///ubuntuforums.org/newthread.php?do=newthread&f=334]("http:///ubuntuforums.org/newthread.php?do=newthread&f=334")

Playback of sound is not a problem. Playback of CDs, streaming internet audio (Pandora, PBS, and so forth) is perfect. No Snap, Crackle, Pop as I listen to these playbacks.

The posts of Pulse Audio and Alsa setup said little about recording audio. I've tried many combinations of settings on the pulse audio recording and playback levels thru the volume control of pulse audio and that of the sound icon on the panel. No matter what levels I set for playback, recording, input, etc. It doesn't matter. I still get the static or popping, crackling in the background on playback of the recording.

With my previous installation of Hardy the recordings of audio with Sound Recorder or Audacity were perfect. No popping or static sounds.

My question is - What happened?

Here is the information from

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
Subdevices: 1/1
Subdevice #0: subdevice #0

AND FROM

lspci -vv


02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
Subsystem: Creative Labs Device 1003
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (500ns min, 5000ns max)
Interrupt: pin A routed to IRQ 17
Region 0: I/O ports at df20 [size=32]
Capabilities: <access denied>
Kernel driver in use: EMU10K1X
Kernel modules: snd-emu10k1x

Thanks for any hints or advice

---

### Post by tbraun on 2010-06-07
Did you ever get a solution to this problem? It's the same for me, even with from 9.10 and even now 10.04.

---

### Post by endo on 2010-06-09
The same here.
[http://ubuntuforums.org/showthread.php?t=1505793](http://ubuntuforums.org/showthread.php?t=1505793)

Ubuntu 10.04 / Creative SB Live! - input not working.

---

### Post by lidex on 2010-06-10
Have a look here:
[http://alsa.opensrc.org/index.php/AlsaTips]("http://alsa.opensrc.org/index.php/AlsaTips")
Scroll down to section: 'Tips to Enable Recording'

---

