---
title: "Dummy Sound on Asus X550JK on ubuntu 14.04"
date: 2015-08-25
forum: Multimedia Software
---

### Post by Wojciech_Telus on 2015-08-25
[COLOR=#111111][FONT=Ubuntu]i've got a problem with soundcard on my asus. In sound settings i've got an dummy output against build in speakers. When i out in terminal [/FONT][/COLOR]aplay -l[COLOR=#111111][FONT=Ubuntu] i recieve [/FONT][/COLOR]aplay: device_list:268: no soundcards found...[COLOR=#111111][FONT=Ubuntu] and I've tried reinstall pulseaudio and alsa drivers but all of this for nothing. I've done everything from tuts here and nothing work.Please help![/FONT][/COLOR]

---

### Post by Yellow Pasque on 2015-08-25
```
sudo update-pciids
```

Then, get the sound info and post the link: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

It's possible you need newer ALSA kernel module with this patch: [https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df](https://github.com/torvalds/linux/commit/6ffc0898b29a2811a6c0569c5dd9b581980110df)

---

### Post by Wojciech_Telus on 2015-08-25
[http://www.alsa-project.org/db/?f=6da36f49b5e06c2f4523addea14a4ea5ac7ac189](http://www.alsa-project.org/db/?f=6da36f49b5e06c2f4523addea14a4ea5ac7ac189)

Here's link.

---

### Post by Yellow Pasque on 2015-08-25
First, get rid of this line in /etc/modprobe.d/alsa-base.conf:
```
snd_hda_intel: model=auto
```

Next, install latest kernel sound module/driver: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-lts-utopic-dkms_0.201508241546%7Eubuntu14.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-lts-utopic-dkms_0.201508241546%7Eubuntu14.04.1_all.deb)

See if there's any difference in the alsa info after rebooting.

---

### Post by Wojciech_Telus on 2015-08-26
Nothing change. Here's link after I've added line in [COLOR=#000000] /etc/modprobe.d/alsa-base.conf:

[/COLOR][http://www.alsa-project.org/db/?f=2668328271a229af675d607802c2a9056fc75c61](http://www.alsa-project.org/db/?f=2668328271a229af675d607802c2a9056fc75c61)

---

### Post by Yellow Pasque on 2015-08-26
No, I suggested removing the line

---

### Post by Wojciech_Telus on 2015-08-26
Sorry, I've misunderstood you, here's fixed, but still, nothing change.[URL="http://www.alsa-project.org/db/?f=869bad29e75abebdb5e27de09f4cc339a9c5f9e9"]

http://www.alsa-project.org/db/?f=869bad29e75abebdb5e27de09f4cc339a9c5f9e9[/URL]

---

### Post by Yellow Pasque on 2015-08-27
> [    4.118751] oss_hdaudio: HDA codec 0x14f1510f not known yet

At some point, you installed OSS4 sound system, so uninstall it. Please tell us exactly what you've done to modify the sound, because it seems like you've done a bunch of different, incompatible "fixes" that just made things worse.

---

