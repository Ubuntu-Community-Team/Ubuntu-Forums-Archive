---
title: "Ac3 audio problem"
date: 2009-11-02
forum: Multimedia Software
---

### Post by niccoc1603 on 2009-11-02
Hello!
I am really new to ubuntu world so please help me!!

My PC has an ALC662 audio chipset with 5.1 speaker capabilities,
I just installed Ubuntu 9.04, i've readen a lot of guides and everything seems to be ok, this is the report from aplay -l command:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```also the speaker-test -Dplug:surround51 -c6 -l1 -twav works perfectly

```

speaker-test 1.0.18

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.522997
```
in fact when i play a Mp3 audio file on VLC i can hear the sound from all the 6 speakers.

But i have a problem when i play movies with AC3 audio stream. In fact i can hear the audio from the 6 speakers, but instead of having the speech from the central speaker, the surround from the rear speakers how it should be, I have the same track from all the speakers!. 


I tried to  set 5.1 on VLC from Audio>Audio Device but i get this error:
```

Audio output failed:
The audio device "surround51" is already in use.
Audio output failed:
VLC could not open the ALSA device "surround51" (Device or resource busy).
```what can i do in order to listen a proper AC3 audio stream? 
please help me!!!

thank you!

---

### Post by lancerocke on 2010-05-08
same problem

---

### Post by lidex on 2010-05-08
Are you using spdif or hdmi output?

---

### Post by lancerocke on 2010-05-08
> **lidex said:**
> are you using spdif or hdmi output?
hdmi

---

