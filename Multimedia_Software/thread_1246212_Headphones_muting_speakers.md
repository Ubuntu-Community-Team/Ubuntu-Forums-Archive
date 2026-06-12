---
title: "Headphones muting speakers"
date: 2009-08-21
forum: Multimedia Software
---

### Post by Thoork on 2009-08-21
Hey,

So i've done my research and tried milions of different commands on /etc/modprobe.d/alsa-base (which is an empty file, I suppose that is normal...) and I haven't managed to mute the speakers when I plug in the headphones.

Im on Ubuntu 9.04, on a Toshiba Satellite A200-12x notebook. Any help would be great! This is driving me nuts!

Thanks!

---

### Post by Yellow Pasque on 2009-08-21
In Ubuntu 9.04, the file is named alsa-base.conf

---

### Post by Thoork on 2009-08-21
> **Temüjin said:**
> In Ubuntu 9.04, the file is named alsa-base.conf

That's very true, thanks.

However, I tried these commands and i still cant get it:

options snd-hda-intel model=3stack
options snd-hda-intel model=lenovo
options snd-hda-intel model=laptop

Any ideas?

Thanks again.

---

### Post by Yellow Pasque on 2009-08-21
Did you try:
options snd-hda-intel model=toshiba

---

### Post by Thoork on 2009-08-21
> **Temüjin said:**
> Did you try:
options snd-hda-intel model=toshiba

Hey, thanks for the answer. Didn't quite work though... Any other ideas? Thanks. I hope this bug gets fixed at some point.

---

### Post by Nostalos on 2009-08-21
I'm not sure about on your Toshiba laptop, but my Dell desktop has the same issue on a new install with the Intel HD Audio.  For me the fix is to right click the volume control applet in systray and "Open Volume Control"

Go to preference and check the "Headphone Jack Sense".  Which should show up now under the switches tab, check mark it in the switches tab to enable.

---

### Post by Yellow Pasque on 2009-08-21
Maybe upgrading ALSA will help: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Maheriano on 2009-08-21
I just found this option in the BIOS options on the Intel board I was messing with last night. Try that.

---

### Post by Thoork on 2009-08-21
Nostalos, i tried that but I think that's definately not the soruce of the problem.

Temüjin, i'll try the upgrade, that might fix it, but its quite complicated it seems...

Maheriano, sorry, could you specify a bit more on what option in the BIOS?

Thanks a bunch,

EDIT:

I upgraded ALSA to the new version, however, speakers do not mute when I plug in the headphones...

---

