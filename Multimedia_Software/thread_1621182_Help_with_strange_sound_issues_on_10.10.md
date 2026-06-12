---
title: "Help with strange sound issues on 10.10"
date: 2010-11-14
forum: Multimedia Software
---

### Post by mellamanjefe on 2010-11-14
Hello, I installed 10.10 to build a HTPC using the ASUS AT5IONT-I motherboard. I am using the HDMI output to display on a Samsung TV. So far the video signal is great, downloaded the nVidia drivers and the images are crisp and clear. The sound is giving me a headache, mostly because it is missing.

I tried searching through other threads but it seems as if for most other users the problem is that either alsa or Ubuntu fail to detect the HDMI output on their system. This does not seem to be the problem for me:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```And the sound manager lists the devices properly (see attachemnts).

However, when I go to play a video or sound file there is no sound coming out of the speakers.

I have gone through alsamixer and unmuted all of the channels, I also added the user to the audion group but no matter if I am trying the sound test utility or Mythbuntu, to play some sounds I cannot get the HDMI to play through my TV. I do get sound from the front panel of the computer case if I select the analog output option in the sound preferences, so I know my data source is ok. I have also checked the input to the TV and the cable with another PC (windows) and confirmed that the tv input and thecable are good.

In fact, this is where I get stumped. I can actually play sounds through the HDMI output and the TV by doing the following:

```

$aplay -D hw:1,3 track47.wav
$aplay -D hw:1,7 track47.wav
$aplay -D hw:1,8 track47.wav
$aplay -D hw:1,9 track47.wav

```Any of the above will play the track properly from Ubuntu and out the TV.However, if I try to go through card #0:

```

$aplay -D hw:0,0 track47.wav
$aplay -D hw:0,1 track47.wav

```Then I only get sound through the front panel output with the first command above but nothing with the second.


Help please, I feel like this is so close to working but something basic is off and I can't figure it out.

Thanks!

---

### Post by mellamanjefe on 2010-11-14
Alright, I was able to resolve this issue thanks to a post on the xmbc forums. Follow this link and the specific steps that got me up and running are the last comment on that page:

[http://forum.xbmc.org/showthread.php?t=79012&page=32](http://forum.xbmc.org/showthread.php?t=79012&page=32)

---

