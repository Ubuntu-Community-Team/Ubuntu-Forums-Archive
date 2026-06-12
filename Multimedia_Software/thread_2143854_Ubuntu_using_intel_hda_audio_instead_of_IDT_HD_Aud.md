---
title: "Ubuntu using intel hda audio instead of IDT HD Audio"
date: 2013-05-10
forum: Multimedia Software
---

### Post by theperfectpunk on 2013-05-10
Hello,

My Notebook has IDT HD Audio that supports Dolby Advanced Audio v2, I wanted surround control and volume leveling so i installed pavucontrol but the required settings did not appear under configuration. I noticed using hardinfo that ubuntu was using snd_hda_intel instead of IDT HD Audio (it's something like IDT 92xxxx ish).

I also got the output of wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh --upload here : [http://www.alsa-project.org/db/?f=bb72a8c9521f5704a02b6db9ad24a06df29b3b63](http://www.alsa-project.org/db/?f=bb72a8c9521f5704a02b6db9ad24a06df29b3b63)

How can i install the correct drivers so that i can use get the options of Volume Leveling and Surround Sound coz the sound is really awfull as compared to Windows 8

---

### Post by Yellow Pasque on 2013-05-12
snd-hda-intel is the correct driver. Most devices conform to this standard nowadays: [http://en.wikipedia.org/wiki/Intel_High_Definition_Audio](http://en.wikipedia.org/wiki/Intel_High_Definition_Audio)

If you want to try the latest version of the driver, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

