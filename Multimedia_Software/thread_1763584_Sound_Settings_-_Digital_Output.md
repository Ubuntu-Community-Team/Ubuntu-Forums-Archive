---
title: "Sound Settings - Digital Output"
date: 2011-05-20
forum: Multimedia Software
---

### Post by pbrille on 2011-05-20
Hi,

how Do I enable digital audio output (hdmi or coax) on Maverick?
It's a Intel Atom Ion 330 Mini-ITX Board (Point of View).

Honestly, I tried and also searched the web but I don't find the way how it's done.
At first I don't know why there are so many Sound Systems (OSS, Alsa, Pulse).
Which of those is relevant for me?

Edit:
I ran this script
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.shand got this output...
> cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.URRJEL7I2a/alsactl.tmp: No such file or directory


I do have a soundcard... onboard

Regards
Peter

---

