---
title: "Ubuntu 14.04 Headphone and Mic Jacks not Working"
date: 2014-07-17
forum: Multimedia Software
---

### Post by KadrisMieryu on 2014-07-17
I am dual booting Windows 7 and Ubuntu but have a problem with getting Ubuntu to recognize my headphones and mic.It works fine on Windows so it's not a problem with the headset or the jacks.
My Alsa information is at [http://www.alsa-project.org/db/?f=7753956993ae76f3317f259ad28207c6432aaafc](http://www.alsa-project.org/db/?f=7753956993ae76f3317f259ad28207c6432aaafc)

---

### Post by Yellow Pasque on 2014-07-18
The first thing I would do is upgrade to latest ALSA: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If it's not working after reboot, I would try to look at hdajackretask to make sure the jacks are correctly identifed.
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

If it's still not working, file a bug:
```
ubuntu-bug audio
```

---

### Post by KadrisMieryu on 2014-07-19
Thanks for helping. It still doesn't work, and changing the overrides mutes the outputs in alsamixer. I'm gonna try to see if any of the overrides work.

EDIT: I wasn't very clear. The headphones and Line In show up in hdajackretask and the bug submission, but nowhere else. I also discovered that when I plug my headphones into my headset jack the audio works and "Speakers" turns into "Headphones", but when I plug my mic into the same jack it still changes it to "Headphones". So it seems like Linux is trying to use the wrong jack for headphones and nothing works for the mic. I think the headset jack is supposed to be for headsets with a mic that only have one jack, but I've never used it so I'm not sure.

EDIT 2: The headphones and line in that show up on hdajackretask are for the headset jack, but the lint in part of it doesn't work. So the mic and headphone jacks don't show up.

---

### Post by Kristian Hermansen on 2015-01-14
> **KadrisMieryu said:**
> Thanks for helping. It still doesn't work, and changing the overrides mutes the outputs in alsamixer. I'm gonna try to see if any of the overrides work.

EDIT: I wasn't very clear. The headphones and Line In show up in hdajackretask and the bug submission, but nowhere else. I also discovered that when I plug my headphones into my headset jack the audio works and "Speakers" turns into "Headphones", but when I plug my mic into the same jack it still changes it to "Headphones". So it seems like Linux is trying to use the wrong jack for headphones and nothing works for the mic. I think the headset jack is supposed to be for headsets with a mic that only have one jack, but I've never used it so I'm not sure.

EDIT 2: The headphones and line in that show up on hdajackretask are for the headset jack, but the lint in part of it doesn't work. So the mic and headphone jacks don't show up.

Start alsamixer:

$ alsamixer
Hit F5 to show all devices.

Scroll to the right until you find Auto-Mute Mode. Set it to disabled.

---

