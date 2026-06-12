---
title: "Headphone port not working in Ubuntu 12.04"
date: 2015-08-15
forum: Multimedia Software
---

### Post by EnKaIn on 2015-08-15
My headphones/speakers are not working in Ubuntu 12.04. The internal speakers are working just fine. I saw some other people having the same problem and they posted their ALSA code. Here is mine : [http://www.alsa-project.org/db/?f=f0106efe76178b16bae7eb337b7c431db476fe07](http://www.alsa-project.org/db/?f=f0106efe76178b16bae7eb337b7c431db476fe07) 

Please tell me whats wrong with my PC and can this be resolved?

---

### Post by Yellow Pasque on 2015-08-15
I would try updating to latest ALSA kernel module/driver to make sure it's not a problem that has been fixed already.  The package you want is oem-audio-hda-daily-lts-utopic-dkms  [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

---

### Post by EnKaIn on 2015-08-16
> **Temüjin said:**
> I would try updating to latest ALSA kernel module/driver to make sure it's not a problem that has been fixed already.  The package you want is oem-audio-hda-daily-lts-utopic-dkms  [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

I did that. Still not working. I think what happened was, when I had Windows I plugged the headphone into the microphone slot and since then it stopped working. And this has carried on to Ubuntu.

---

