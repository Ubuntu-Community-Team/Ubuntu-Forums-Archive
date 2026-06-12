---
title: "Sound Blaster Live! 1024 OEM - no CD audio, no bass/treble or MIDI adjustment"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by olavi on 2005-12-04
I have SB Live! 1024 OEM. A year ago I used Gentoo and XFCE: CD audio, bass, treble and MIDI adjustment worked just fine. They don't with Ubuntu/Gnome.

For some reason CD volume is in recording tab, and I can't hear anything the CD player plays. Bass and treble settings don't do anything. Plus, for some reason the PCM adjustment bar changes the MIDI music volume, too; Synth doesn't do anything.

What is this? Anyone else noticed the same?

---

### Post by olavi on 2005-12-04
Copied sndstat here. Is that "ADC Capture/Standard PCM Playback (DUPLEX)" correct for my card? Any SB Live! Value owners here - could you please post your "cat /proc/asound/oss/sndstat" here? The Live! Value is 99% like my 1024 OEM and can use the same drivers.

```
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux nurmi3 2.6.12-10-k7 #1 Fri Nov 18 12:46:18 UTC 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
SBLive! Value [CT4832] (rev.8, serial:0x80271102) at 0xdc00, irq 10

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
0: EMU10K1 MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: TriTech TR28602
```

---

### Post by olavi on 2005-12-04
Actually CD audio works, the CD player just had no volume...

However, the main problem still persists: The only mixer settings that work are Master and PCM. Others don't do anything.

---

### Post by mrweirdo on 2006-04-09
I have the same problem myself with my sblive 5.1 xgamer card. Bass or treble controls dont do a darn thing. I'm about ready to give up on linux and go back to windows :/

---

### Post by graigsmith on 2006-04-17
to get bass and treble to work.  you have to enable tone.

to get distortion free bass, you must turn the "wave" channel to half volume.  not the pcm or any other channel, it must be exactly the wave channel.

---

