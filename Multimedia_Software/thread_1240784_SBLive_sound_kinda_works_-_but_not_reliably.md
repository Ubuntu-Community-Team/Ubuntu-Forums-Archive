---
title: "SBLive sound kinda works - but not reliably"
date: 2009-08-15
forum: Multimedia Software
---

### Post by horuskol on 2009-08-15
I installed Ubuntu/Gnome for the first time ever a couple of weeks or so ago.

Everything seems okay - but I'm wanting to be able to listen/manage my music collection and having trouble getting Amarok (and other players) to use my soundcard.

I checked my sound preferences - playback and music are both set to:
```

SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) Multichannel Playback (ALSA)

```
and the test works - but most Gnome desktop sounds still seem to be coming through the PC speaker, and Amarok ad RhythmBox are silent.

I also have "Multichannel Capture/PT Playback" as an option - although no sound from the test, and also "ADC Capture" - but that throws an error on test.


I searched and discovered [https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/074661.html](https://lists.ubuntu.com/archives/kubuntu-bugs/2009-May/074661.html) so I installed the kdebase-workspace package. I only have the ADC Capture device type, and the test fails.

Anyone know how I can get the Multichannel Playback device as an option in the kdebase-workspace options? I hope that will then let Amarok play my music.

TIA - HK

---

