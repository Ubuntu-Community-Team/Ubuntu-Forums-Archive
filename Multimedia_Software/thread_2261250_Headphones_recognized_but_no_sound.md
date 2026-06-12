---
title: "Headphones recognized but no sound"
date: 2015-01-17
forum: Multimedia Software
---

### Post by Marie_Venneman on 2015-01-17
I'm new to Linux so I have very little experience. 

I have Ubuntu 14.04.1 LTS installed on my computer (single-boot install). Speakers work fine but when I plug in headphones the computer recognizes it but I get no sound. I checked the settings and it's not muted. I used the headphones on other devices and that works fine. 

I've tried different suggestions but so far nothing worked.

---

### Post by Yellow Pasque on 2015-01-17
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Marie_Venneman on 2015-01-18
[http://www.alsa-project.org/db/?f=01082b9a950aeb6e539b0bd3a776dd0f50b5277e](http://www.alsa-project.org/db/?f=01082b9a950aeb6e539b0bd3a776dd0f50b5277e)

---

### Post by Yellow Pasque on 2015-01-19
It looks like you have already tried some fixes:
```
snd_hda_intel: model=eapd probe_mask=1 position_fix=1
```

The model=eapd should be unnecessary (It should done automatically in modern kernels: [https://github.com/torvalds/linux/commit/cb766404e6b8c566569eb9ada02ea45d28729864](https://github.com/torvalds/linux/commit/cb766404e6b8c566569eb9ada02ea45d28729864) )

So, try the latest sound module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If it's still not working after reboot, then I'd suggest filing a bug at: [https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)
Another owner of Satellite P205 also has no headphones: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1407026](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1407026)

---

### Post by Marie_Venneman on 2015-01-19
I installed the latest modules/drivers and still no change after reboot. I'm filing a bug next.

---

