---
title: "volume buttons don't work, but panel volume does?    (Jaunty)"
date: 2009-08-06
forum: Multimedia Software
---

### Post by theromanone on 2009-08-06
I increased some of the values in "alsamixer" in the terminal, pretty sure the volume control settings were not changed, and all of the sudden now when I press my Volume Increase/Decrease/Mute buttons the volume thing comes up and shows it being muted/increased/decreased but the volume does not change whatsoever.

To change it, I have to actually go to the panel's volume and control it from there, where it works flawlessly. Any ideas?

---

### Post by theromanone on 2009-08-07
anyone??

---

### Post by hugoheden on 2009-08-12
> **theromanone said:**
> I increased some of the values in "alsamixer" in the terminal, pretty sure the volume control settings were not changed, and all of the sudden now when I press my Volume Increase/Decrease/Mute buttons the volume thing comes up and shows it being muted/increased/decreased but the volume does not change whatsoever.

To change it, I have to actually go to the panel's volume and control it from there, where it works flawlessly. Any ideas?

I looks like we're having the same problem, though I am on Intrepid. (Pressing a multimedia button (mute, increase volume, decrease volume) makes the correct GUI-notification appear, but does not have an effect on the actual sound.)

One compelling option would perhaps be to completely reinstall sound from scratch, but how would one do that? There is a bug report[1] suggesting the following, but I am not sure it is safe and up to date?? Also it uses aptitude while I usually use apt-get.. would there be a compatibility problem of some kind??

[B]sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
[/B]

[1] [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/314635](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/314635)

---

