---
title: "Sound not working"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by fourthofjuly on 2007-07-15
**Sound works in Windows XP, but not in Ubuntu 7.04, Fedora 7 and OpenSuSE 10.1. No sound at all.**

[LIST=1]
[*]I have an Intel D845GCL original motherboard with on-board sound, Pentium D 3.0 GHz, 160 GB SATA HDD & 1GB RAM. 

[*]In Ubuntu sound preferences, under Default Mixer Tracks, listed device are HDA Intel (ALSA mixer) and SigmaTel STAC9221 A1 (OSS Mixer).

[*]I have tried disabling sound from BIOS, applied the latest updates of Fiesty, but nothing seems to work.
[/LIST]

Could anyone be kind enough to guide me in making sound work on my system?

Thanks & With Warm Regards,

Devang.

---

### Post by usergentoo on 2007-07-15
I have a similar card try this. It may or may not work.

Add these lines to the end of /etc/modprobe.d/alsa-base

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

---

### Post by fourthofjuly on 2007-07-15
**/etc/modprobe.d/alsa-base file appended with the two lines suggested.**

**Result**: sound volume control icon got disabled & message "gstreamer plugin required or sound card not configured" something like that.

System enabled sound icon after I removed the two lines - but no sound again.

Please help.

With warm regards,

Devang.

---

### Post by fourthofjuly on 2007-07-17
**Sound works in Windows XP, but not in Ubuntu 7.04, Fedora 7 and OpenSuSE 10.1. No sound at all.**

[LIST=1]
[*]I have an Intel D845GCL original motherboard with on-board sound, Pentium D 3.0 GHz, 160 GB SATA HDD & 1GB RAM. 

[*]In Ubuntu sound preferences, under Default Mixer Tracks, listed device are HDA Intel (ALSA mixer) and SigmaTel STAC9221 A1 (OSS Mixer).

[*]I have tried disabling sound from BIOS, applied the latest updates of Fiesty, but nothing seems to work.
[/LIST]

Could anyone be kind enough to guide me in making sound work on my system?

Thanks & With Warm Regards,

Devang.

---

### Post by acaby on 2007-07-18
I have Ubuntu 7.04 and my sound worked perfectly UNTIL I installed the updates from the update manager. (about 180mb)


Try this fix:

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

I did this and my sound came back after reboot. I think there must have been a bug in one of the update files.
In case the below fix will not work for you, however it should, You can find the Complete solution from this post:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
You may want to look at it just in case you see a solution that may work for you other than the one I have suggested below

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot

VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot


Hope this helps
Good Luck,
Arthur

---

### Post by radj2 on 2007-10-04
You go to Sound in Ubuntu preferences and no matter what you try - your selection for a default sound card will not stick! No need to fear. Just watch the video above and use the following scripts. Copy each script, then right click on you desktop and choose create document. Paste each script in there. Once the correct card name has been pasted into the script (you’ll likely want a script for the sound card and for the headset if needed), you are half way there. Right click on it afterward and then goto properties, choose permissions then allow to be executed.

What sound cards do you have? Open up a terminal and paste in:

sudo asoundconf list

Make note of each card. Use trial and error if you are unsure which card is which. The process of elimination will only take a few tries.

#! /bin/sh -f

sudo asoundconf set-default-card name-of-card-to-be-default

This worked for me,finally

---

