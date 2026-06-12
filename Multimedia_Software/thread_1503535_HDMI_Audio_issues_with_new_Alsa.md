---
title: "HDMI Audio issues with new Alsa"
date: 2010-06-06
forum: Multimedia Software
---

### Post by Cheator on 2010-06-06
Summary of problems in this post:
1. At startup, sound doesn't work until I fiddle with gstreamer-properties
2. Right channel louder than left

Hey gang.

So I finally got my Nvidia 210 working with HDMI audio by updating to alsa 1.0.23. Now that that works, however, It seems that on startup my sound doesn't work properly...

This is a list of what I did from install of Ubuntu 10.04:

1. Upgraded Alsa
2. Switched ubuntu from pulseaudio to alsa using gstreamer-properties
3. Tested the HDMI sound cards (it lists 4 of them)
4. Ran XBMC and it worked.

Now every startup, I have to oepn gstreamer-properties, set the default card from the third Nvidia HDMI to any other HDMI.. then back again. Bam, it works fine after that. Also, 

Any idea how i can troubleshoot this?

I also have the issue where the right channel is louder than the left for some reason.. any ideas?

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

For the record, 7 is the one that works... i'd like to find a way to get rid of the rest of them.

Thanks!

---

### Post by Jinger on 2010-06-09
I had had the same problem, but then I solved. Follow me:
Click on "System" left on the top then on preferences and in the end on "Audio". Audio configuration page will open:
[IMG]http://img3.imageshack.us/img3/8329/audiocz.png[/IMG]

Go to "Hardware" and at the bottom of the page there's "profile". Select "Digital Stereo (HDMI) output":
[IMG]http://img532.imageshack.us/img532/9041/audio1.png[/IMG]

---

### Post by Cheator on 2010-06-10
No i don't have a choice of those, its simply one choice. Also, its going to a TV so it has t obe non digital

---

### Post by Jinger on 2010-06-10
Do you have to use it needs? When my Netbook didn't work with HDMI port I used a cable similar to this:
[IMG]http://www.angelipc.it/08112_0000.jpg[/IMG]

---

