---
title: "help needed with setting up midi device ToneLab SE"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by gosh on 2007-01-09
Hi, I hope someone can help me with getting the SoundEditor for my Vox ToneLab SE guitar floorboard to work. (With this software I can store patches of different guitareffects on the floorboard)

The Tonelab is connected through Midi In and Out to my computer. I use a Midiman Midisport 1x1 USB interface.
```
jos@jos-desktop:~$ amidi -l
Device    Name
hw:0,0    EMU10K1 MPU-401 (UART)
hw:0,1    Emu10k1 Synth MIDI (16 subdevices)
hw:0,2    Emu10k1 Synth MIDI (16 subdevices)
hw:3,0,0  Midisport 1x1 MIDI 1

```The SoundEditor software is installed using Wine. It actualy works! (see screenshot). But only partially.
Does work: changing a patch. I can adjust any parameter and write it to the floorboard.
DOESN'T WORK: reading a patch. I cannot read the already programmed patches from the floorboard to the SoundEditor. 

There must be something wrong with the Midi-setup.
When I start the SoundEditor application in wine it shows:

```
MIDI communication error occured.
Check the cables and MIDI interfaces
```The terminal shows:
```
jos@jos-desktop:~/.wine/drive_c/Program Files/ToneLabSE SoundEditor$ wine SeTnLbSE.EXE
err:midi:MIDI_AlsaToWindowsDeviceType Cannot determine the type (alsa type is 100000) of this midi device. Assuming FM Synth

```Is there anyway to debug this or one way or the other find out what actually is send to and fro?
I try to use gmidimon but that did not gave me any readings.
What other info should I give you to help me?

Thanx

---

### Post by gosh on 2007-01-10
Oops, forgot the screenshot

---

### Post by gosh on 2007-01-12
* bump *

---

### Post by gosh on 2007-04-30
Midi is much improved under wine 0.9.36.
It now works
!:guitar:

---

