---
title: "Loud and distorted sound through external audio interface"
date: 2017-03-19
forum: Multimedia Software
---

### Post by ersten on 2017-03-19
I think that I have problem with software with the external USB audio interface. I have a very loud and very distorted sound.
My setup is Ubuntu 14.04.4; USB interface Gustard U12; Lite DAC-AH.


aplay -l:
```
card 0: MID [HDA Intel MID], device 0: 92HD81B1C5 Analog [92HD81B1C5 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: x20 [xCORE USB Audio 2.0], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


```

I used Clementine and everything worked fine. But I decided try to use mpd. At the first time everything worked perfectly too, but after suspend PC sound is disappered. There was no errors or something else, anything looks fine, but there was no sound.


I tried many such commands as (I found this on the forum):
```
amixer set -c 0 Master 255 unmute

```I tried with various combinations of this command with other devices, but nothing happened. But answer is about 'maximum level is 127':
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [on]

```


Somehow I found one of the GUI-mixer (GNOME ALSA mixer), where was Mute checkbox on my device. When I turned off this Mute, the sound appeared but it is very loud and distored.
This sound persist if I connect this audio interface to the another PCs. It looks like a trouble with the audio interface, not with Ubuntu.


I think that somehow I raised the output level to too hight in the audio interface. I tried commands like 
```
amixer set -c 0 Master 100 unmute
```, I tryed to lower the level by a lot of GUI-mixer and alsamixer. But nothing change.


How can I make the output lever lower?

Thanks for your help! And sorry for my poor English.
Alek.

---

