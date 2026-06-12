---
title: "XPS 13 Ubuntu 16.04.02 no sound"
date: 2017-06-22
forum: Multimedia Software
---

### Post by sgyang on 2017-06-22
I feel like I've tried all the answers but no luck in solving the problem. I fresh installed Ubuntu 16.04.02 LTS everything was working fine except sound. This is the output of aplay -l
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Only HDA Intel HDMI is detected, and I've no idea why. Any help is appreciated!

---

### Post by vasa1 on 2017-06-23
I'm going to post my own audio worries in another thread but can you get audio with mpv?

```
sudo apt-get install mpv
```

mpv works for me for audio whereas both vlc and gnome-mplayer don't. I'm also on 16.04.2.

---

### Post by Yellow Pasque on 2017-06-23
Get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

