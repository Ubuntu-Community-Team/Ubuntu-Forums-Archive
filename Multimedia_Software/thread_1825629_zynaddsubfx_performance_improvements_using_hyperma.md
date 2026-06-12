---
title: "zynaddsubfx performance improvements using hypermatirx preset"
date: 2011-08-15
forum: Multimedia Software
---

### Post by BcRich on 2011-08-15
Hi
can any1 make a suggestion as to how i can get the performance of zynaddsubfx to improve when using the hypermatrix preset from William_Godfrey_Collection?
basically the sound from zyn starts like "scraping" or sounding distorted (kind of like a clipping effect). I know this is not related to levels though, but related to the sound not being processed in time especially when I have a lot of short notes played together ( i get major xruns in JACK when this happens). my frames/buffer in JACK are set to 128 and periods/buffer set to 3. changing these settings does not seem to have any effect. I also tried changing the internal sound buffer size samples in zyn (which are currently at 256), but this had no noticable effect either.
When using the hypermatrix preset which is triggered from rosegarden, Rosegarden will also sometimes complain that it does not have enough processing power for realtime playback and playback will halt. i then click play again and the track continues to play from the place it halted at.
given that the track in question does have a fair amount of midi data, make use of zyn, ardour (about up to 4 to 6 simultaneous tracks, one or two which have effects) and rosegarden to trigger all the midi (which is routed to an eternal drum machine and 2 zyn channels). 
Is this load seriously going to blow out my system? a hex core AMD 1075t with 8GB RAM. I'm using ubuntustudio 10.10 x64 and I don't have any apps running beside the music making stuff.
Would really appreciate some feedback and/or options. thanks!

---

### Post by BcRich on 2011-08-16
any help on this wold really be appreciated
rosegarden completely stops playing in the middle of the track (that I'm making), saying that it does not have enough resources for realtime processing. I find this difficult to believe since I'm using a 6 core amd processor , 8 GB's of RAM and an external Lexicon Omega sound device.
here's sequencer details from rosegarden
```
 p, li { white-space: pre-wrap; } Rosegarden 10.02 - AlsaDriver [ALSA library version 1.0.23, module version 1.0.23, kernel version 2.6.35-30-generic]
  JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 128
 JackDriver::initialiseAudio - creating disk thread
 JackDriver::initialiseAudio - found 2 JACK physical outputs
 JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "system:playback_1"
 JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "system:playback_2"
 JackDriver::initialiseAudio - found 4 JACK physical inputs
 JackDriver::initialiseAudio - connecting from "system:capture_1" to "rosegarden:record in 1 L"
 JackDriver::initialiseAudio - connecting from "system:capture_2" to "rosegarden:record in 1 R"
 JackDriver::initialiseAudio - initialised JACK audio subsystem
    ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
  Using low-resolution system timer, sending a warning
     Current timer set to "system timer" with timer checks
     WARNING: using system timer with only 100Hz resolution!
 AlsaDriver::initialiseMidi -  initialised MIDI subsystem
  Using low-resolution system timer, sending a warning
     Current timer set to "system timer" with timer checks
     WARNING: using system timer with only 100Hz resolution!
 AlsaDriver::setPlausibleConnection: connection like "" requested for device 0
 AlsaDriver::setPlausibleConnection: fuzzy match 129:0 ardour: control (duplex) available with fitness 1
 AlsaDriver::setRecordDevice - successfully subscribed device 1 as record port
 AlsaDriver::setPlausibleConnection: connection like "" requested for device 1
 AlsaDriver::setPlausibleConnection: fuzzy match 129:0 ardour: control (duplex) available with fitness 1
    ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     131,0 - (Hydrogen, Hydrogen Midi-In)		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]
     ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     131,0 - (Hydrogen, Hydrogen Midi-In)		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]
     133,0 - (ZynAddSubFX, ZynAddSubFX)		(WRITE ONLY) [ctype 1, ptype 1024, cap 66]
  AlsaDriver::setPlausibleConnection: connection like "20:0 Lexicon Omega MIDI 1 (duplex)" requested for device 2
 AlsaDriver::setPlausibleConnection: exact match available
 AlsaDriver::setPlausibleConnection: connection like "133:0 ZynAddSubFX (write)" requested for device 3
 AlsaDriver::setPlausibleConnection: exact match available
    ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     131,0 - (Hydrogen, Hydrogen Midi-In)		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]
     133,0 - (ZynAddSubFX, ZynAddSubFX)		(WRITE ONLY) [ctype 1, ptype 1024, cap 66]
     ALSA Client information:
      14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
     20,0 - (Lexicon Omega, Lexicon Omega MIDI 1)			(DUPLEX) [ctype 2, ptype 589826, cap 127]
     129,0 - (ardour, control)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,1 - (ardour, mcu)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     129,2 - (ardour, seq)			(DUPLEX) [ctype 1, ptype 1179650, cap 99]
     131,0 - (Hydrogen, Hydrogen Midi-In)		(WRITE ONLY) [ctype 1, ptype 1048576, cap 66]
     133,0 - (ZynAddSubFX, ZynAddSubFX)		(WRITE ONLY) [ctype 1, ptype 1024, cap 66]
  
```

---

### Post by madeinfamous on 2011-08-18
allo BcRich


edit the launcher of zynaddsubfx like this (maybe different for you):

```
taskset 0x00000002 /usr/bin/zynaddsubfx

```

this tell zynadd... to use my second processor, 

hope that help,

have a nice day

---

### Post by BcRich on 2011-08-18
> **madeinfamous said:**
> allo BcRich


edit the launcher of zynaddsubfx like this (maybe different for you):

```
taskset 0x00000002 /usr/bin/zynaddsubfx

```this tell zynadd... to use my second processor, 

hope that help,

have a nice day
Hi madeinfamous
thanks for the reply :)
your suggestion does seem to have helped, but i still get the same clipping/distorted/scratchy effect when using the hypermatrix and exterme william godfrey presets.

the same error message gets repeated over and over again from zyn
```
JackActivationCount::Signal value = 0 ref = 3
```
do you have any idea what it's talking about?
thanks again for your help :)

---

