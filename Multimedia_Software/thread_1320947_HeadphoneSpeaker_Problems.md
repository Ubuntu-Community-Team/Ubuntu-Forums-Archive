---
title: "Headphone/Speaker Problems"
date: 2009-11-09
forum: Multimedia Software
---

### Post by zspace on 2009-11-09
I upgraded my 9.04 install to 9.10 last week, and was surprised to find that my audio no longer worked correctly (I've used 7.10-9.04 with no problems at all). I get perfect sound quality, from both my speakers and my headphones, but when I plug in my headphones my speakers continue to play along side my headphones (ie both are outputting the same sound).
So I decided that it might be a glitch left over from the update and did a fresh install from a 9.10 disk. Same problem with the fresh install.
I've spent the last few days trying to fix the thing myself, and surfing the forums trying to find if someone else had a solution, but I have yet to find one that works for me, so I'm posting here.

**What I've tried so far:**
Downloading the latest drivers for Linux from the Realtek web page. This just broke my sound all together
Upgrading to the latest ALSA version (1.21) using the script [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

I tried some of the things suggested [here]("http://ubuntuforums.org/showthread.php?t=806620"). Half the things there are out of date, but I was able to feel my way around to most of the solution (still didn't fix my problem). Here's some of the output from that solution:

```
head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI

```
I'm only using the analogue part, so I'm not really worried about the HDMI or the SPDIF digital part of the Realtek card. The only thing that confuses me is that according to Biostar (my motherboard manufacture) the Realtek card built into my board is a ALC888S not a ALC1200. aplay points out the same thing, but again I'm not sure what type it is.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If anyone has any suggestions as far as what to try (if it worked for you it might work for me :D), or anything at all really, it would be helpful, because I'm out of ideas. I'm running the x64 version if it matters and I have all the updates as of 9AM today.

I'm sure there's about a 1000 threads like this running around, but none of them have helped so...

---

### Post by zspace on 2009-11-15
After 6 days of me being sick and no replies...
BUMP!

---

### Post by prince2689 on 2009-12-27
i had the same problem with my lenovo 3000N100 laptop.....................

i found a solution and it worked for me....................

hope it works for you........

goto [http://ubuntuforums.org/showthread.php?p=8564410#post8564410](http://ubuntuforums.org/showthread.php?p=8564410#post8564410) :lolflag:

---

