---
title: "rPi2 -&gt; rPi3"
date: 2016-06-10
forum: Mythbuntu
---

### Post by john562 on 2016-06-10
Hi,

I've been running Mythbuntu on an rPi2 for some time now. Mostly it's good, but there's one big problem. Watching TV (or even a recording) whilst another recording is in progress will screw up that recording (it glitches every couple of seconds during playback).

I purchased an rPi3 hoping that it might improve perf and thereby rectify the problem above. However, moving my SD card from rPi2 to rPi3 just results in a colorful image on boot (and another smaller colorful image in the top-right corner). I understand this might have something to do with drivers and such, but am unsure how to rectify. I've done a full `apt-get upgrade` and `apt-get dist-upgrade`, but that hasn't helped.

Can anyone tell me:

1. How to migrate from rPi2 image to rPi3 compatible image?
2. Might this actually fix my problem?

Thanks

EDIT: I just realized I probably installed mythbackend manually into Ubuntu rather than Mythbuntu itself (which I don't think supports rPi).

---

### Post by novellahub on 2016-06-21
You may need to update the firmware for your Raspberry Pi.  

```
sudo rpi-update
``` 

Try that and see if it boots in the Raspberry Pi 3.

---

