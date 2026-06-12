---
title: "Do i need Pulse Audio? Want full pass-through sound over toslink (SPDIF)"
date: 2010-04-30
forum: Multimedia Software
---

### Post by schildpad on 2010-04-30
I've installed Ubuntu 10.04 on my HTPC. Asus mb a4m785g with ati 4200.
Problems are dealing with sound. I want all sound to go over toslink (SPDIF) to my AV receiver and let all decoding take place there.

I've been doing a lot of reading...so far I understand pulseaudio is still buggy, so my question is do I need PA at all? Is ALSA able to just pass-through all sound to toslink (SPDIF) straight into the AC-receiver?

I always use my AV-receiver for handling sound (Stereo, DD, DTS ect...)

Does anyone have the solution for me? 
Thanks.

Greetings Sven

---

### Post by aceracer24 on 2010-04-30
Good luck. I have been trying to do this to some extent for awhile as well as trying to solve an issue related to digital sound in general [here]("http://ubuntuforums.org/showthread.php?t=1464623"). I have gotten one reply which didn't really help much. Alot of people have said you can remove pulseaudio but I have seen a lot of people have problems with removing it.

---

### Post by xzero1 on 2010-04-30
_Toslink is only multi-channel when used with a multi-channel source!_ That is the channels must be encoded over toslink into ac3,dts etc unless the source was pre-encoded.

Don't know if it will work for you but I will give it a shot. Follow this example:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Now I want to use my CMI8768 card's spdif output so I need card 0 and *device *2.

Using mplayer syntax, I can then play a 5.1  spdif file by this command:
```

mplayer -ao alsa:device=hw=0.2  -ac hwdts,hwac3 heart.ts
```Note that this on on Ubuntu 10.04 (Lucid) with standard mplayer. No removal of pulse audio necessary.

---

