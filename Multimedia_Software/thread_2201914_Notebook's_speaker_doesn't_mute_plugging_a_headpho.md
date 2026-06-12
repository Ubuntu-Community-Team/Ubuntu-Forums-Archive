---
title: "Notebook's speaker doesn't mute plugging a headphones"
date: 2014-01-26
forum: Multimedia Software
---

### Post by tamashumi on 2014-01-26
Asus B23E notebook - on windows everything works as it suppose to.
On Ubuntu 12.04 LTS I have this common issue I can't make speaker to auto-mute when headphones connected.

I did added the following line at my /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=auto

I've already been through installation of DKMS according to this guide: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

I did checked Auto-Mute mode at alsa mixer, it keeps loosing the tick on the checkbox though

I was searching for any other solution and trying a few different approaches but with no result.
Any help would be greatly appreciated.

I may add that my headphones jack is combo with s/pdif and that if I stick headphones jack half-away then speaker gets muted. But when it's plugged up to the end properly the speakers turns on again.

Here is my alsa info: [http://www.alsa-project.org/db/?f=1cd906d9df9a5681a4e11849c9a0a0408daeb964](http://www.alsa-project.org/db/?f=1cd906d9df9a5681a4e11849c9a0a0408daeb964)

---

### Post by Yellow Pasque on 2014-01-26
Have you tried playing with this switch (in alsamixer)?:
```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
```

---

