---
title: "Weird sound problem"
date: 2013-03-07
forum: Multimedia Software
---

### Post by brabender on 2013-03-07
I'm running Ubuntu Studio (XFCE) 12.04 with MATE on top. Today I booted it up and there was no sound through the analog output. Checked everything and sound card was detected fine, no mute, etc... I booted up Windows 7 on the same computer and sound was OK. As this system has an old hard drive that still has Ubuntu 10.04 installed on it, I booted it up, and also there was no sound. In 10.04, with Gnome 2, I checked gnome-alsamixer, and, as it happened sometimes before, the IEC958  checkbox was set, I unchecked it and sound came back OK. I never toggled it, but it has happened often in the past that it checked itself, perhaps after upgrading kernels. I booted up again 12.04, installed gnome-alsamixer and IEC958 was also set, unchecking the box solved also the sound problem. After that I found that I could have done the same thing in the MATE volume control applet, by default the IEC958 switch was hidden until I enabled it in Preferences.

My question is: how the IEC958 toggle changed itself in both Ubuntu installs? The 12.04 one is my main system, and it's updated almost daily. I usually don't boot up the 10.04 one, I just use the hard disk it's installed onto as a backup disk. I don't remember updating kernels in it in the recent past. In 12.04, my last changes were installing mdm as lightdm substitute. I don't understand how both systems suffered the same problem at the same time. It's mostly curiosity, but I find that the IEC958 problem annoying, specially when it happens after some months and I don't remember quickly this issue

Thanks, and excuse my english.

---

