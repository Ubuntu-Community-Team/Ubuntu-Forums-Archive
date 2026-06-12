---
title: "What am I missing? sound prefs different, no pulse move stream"
date: 2010-05-01
forum: Multimedia Software
---

### Post by lindsayward on 2010-05-01
Hi there,
(Ubuntu 10.04, 2.6.32-21-generic Kernel)
  I just want to send rhythmbox output to my analogue audio output and everything else out my HDMI. I can change sound cards in the main properties (set default), but can't see how to change it for some things - or ever see two at once.
When I search for things, I find other ubuntu users have different options that I don't have, specifically:
My System > Preferences > Sound panel has:
- Sound Effects, Hardware, Input, Output, Applications 
whereas, other people have more options where they can set the device for "Music and Movies" and other things, like the screenshot at this page:
[http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/915-pulseaudioubuntu804](http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/915-pulseaudioubuntu804)

And in the pulseaudio volume control, other people can right-click on a playing source and choose "Move Stream". 
All I see is "Terminate Playback".

I did uninstall pulseaudio earlier to get mythtv to work, but now I've reinstalled it (and have gstreamer and some other things). 
I don't have the files .asoundrc or asound.conf, but I've read that I shouldn't need them.

Here's an output of aplay -l if that's relevant. 
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```I appreciate any help!!

---

### Post by xzero1 on 2010-05-01
Download pavucontrol (pulse audio volume control) for these functions.

---

### Post by lindsayward on 2010-05-01
Thanks very much, but I've got that package. That's what I was using when I right-clicked and only got "Terminate" instead of "Move". I've installed all of the pulse gui things I could find that looked useful.
Is there some sort of reinstall method or something that might be useful?

---

### Post by xzero1 on 2010-05-01
I think you are only allowed to move the stream between cards, not between the card's sub devices. Your aplay -l only shows only one sound card. It may be possible to configure rythmbox. I have done something similar with Nexuiz. The sound preferences that you see is an older version not Lucid.

---

### Post by lindsayward on 2010-05-02
Thanks. I saw that the screenshot was from version 8 or something, but I figured there might be more to it than that since I have fewer options and no way I can see of setting different things for different sound devices - it's one at a time.
Does anyone know how to setup different apps to go to different devices, specifically rhythmbox?
Thank you!

---

### Post by lidex on 2010-05-02
This may help?
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by xzero1 on 2010-05-02
Rythmbox uses gstreamer. Run gstreamer-properties and select OSS sound system (alsa doesn't work for me). Hit the test button and you should hear sound from the analog device. The problem is when I run rythmbox afterwards I hear sound via my default digital device. I think there are still bugs to work out. My guess is pulse audio is the culprit here. Still with a little hacking, I think you might get somewhere.

An easier approach would be to use a different player. As I understand it Amorak supports selection of the audio sink.

---

