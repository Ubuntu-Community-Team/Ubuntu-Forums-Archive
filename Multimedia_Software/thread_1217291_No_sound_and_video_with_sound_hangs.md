---
title: "No sound and video with sound hangs"
date: 2009-07-19
forum: Multimedia Software
---

### Post by runesvend on 2009-07-19
Hi all

I have a strange problem with Ubuntu that I can't figure out myself, so I'm hoping someone here can help me with it.
The problem is as follows:

- There is no sound on my system. Not even if I go into Preferences->Sound and press the Test-buttons does it produce any sound.

- When playing video while enabling sound output, it produces no sound and it hangs after, maybe, half a second of playback. Using mplayer I can seek forward in the video fine and about half a second of the video will play and then hang again.

- When playing video while disabling sound (using the -nosound option in mplayer) the video plays fine and doesn't hang.

- When trying to play audio in Amarok no sound is produced, but the same symptom as using mplayer with sound enabled is present. About half a second it will play the audio (not producing sound but I can see the bars in the visualization-area move up and down) and then hang. Here Amarok seems very sluggish and hangs for, perhaps, 10 seconds each time I try to play a song.

- The audio streams (from mplayer and Amarok) appear in pavucontrol.

Any ideas?

My sound card is a "Terratec Aureon Space 7.1". This is the output of lspci -vvnn):

```
04:03.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
        Subsystem: TERRATEC Electronic GmbH Device [153b:1145]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64
        Interrupt: pin A routed to IRQ 22
        Region 0: I/O ports at bf00 [size=32]
        Region 1: I/O ports at be00 [size=128]
        Capabilities: [80] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: ICE1724
        Kernel modules: snd-ice1724

```

The sound worked fine about a week ago, so I'm not sure what has happened since then.

---

### Post by igorzwx on 2009-07-19
ask markbuntu

---

### Post by runesvend on 2009-07-19
Thanks for your input igorzwx.

I had started a couple of days ago to use the hibernate function instead of turning off my PC, because this function now works and it didn't when I tried to use it a while ago.
So after messing with some configuration files I decided to restart my PC because I couldn't find a way to restart the pulseaudio daemon. And now the sound works :). I've changed the configuration files back to the default and it still works, so a simple restart did the trick. I hadn't thought of that...

Thanks for your time though.

---

### Post by igorzwx on 2009-07-19
aplay -l

man aplay

---

