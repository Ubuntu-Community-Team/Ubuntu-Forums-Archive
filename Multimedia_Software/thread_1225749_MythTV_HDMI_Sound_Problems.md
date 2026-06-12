---
title: "MythTV HDMI Sound Problems"
date: 2009-07-28
forum: Multimedia Software
---

### Post by zzzBrett on 2009-07-28
I have a motherboard with integrated nvidia HDMI that I would like to output both video and sound for an HTPC.  With the help of the mythtv wiki and other forums, I managed to get my sound working through the HDMI output (outside of mythtv).  The only thing I have to do to get the sound working is to enable the switch for "IEC958 1", or run the command ```
amixer set IEC958,1 on

```

After I do that, all sound works fine.

Now, I'm trying to get it working in mythtv and am having some problems.
I've tried using Allen's Digital Audio Howto ([AllensDigitalAudioHowto - MythTV](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)).

I've tried setting my /etc/asound.conf to all of the suggestions, but haven't been successful yet.  The HDMI is card 0, device 3, so I got the following command to work:
```
mplayer -ao alsa:device=hw=0.3 -afm hwac3 test.mp3
```


My MythTV Settings are as follows:
```
Audio output device: ALSA:default
Passthrough output device: Default
Max Audio Channels: Stereo (MUST BE SET TO STEREO as of 6/2/2009 for passthrough to work)
Upmix: Passive
Enable AC3 to SPDIF passthrough checked
Enable DTS to SPDIF passthrough checked
Aggressive sound card buffering off
Use internal volume controls off

```


...but I have tried many other configurations / combinations.  But it seems with four possibilities for the asound.conf file, eight or so possible combinations for the mythtv settings, I can't possibly try every one!



aplay -l gives:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



Any suggestions on how to proceed would be great.

---

### Post by zzzBrett on 2009-07-29
impatient bump :)

---

### Post by zzzBrett on 2009-07-30
Suggestions?

---

