---
title: "Totem &amp; Flash playback now at double speed.."
date: 2010-10-27
forum: Multimedia Software
---

### Post by steveb3210 on 2010-10-27
This was working a few days ago - so I'm thinking an update might be the culrpit.

Ubuntu 10.10 on AMD 64.  ATI RV710 video card.  

Flash & Totem now playback at double speed.   MP3 audio and Flash Videos both exhibit the same behavior.  Tried a plain old reboot - no change.  Looking at the diff between dynamic libaries of libflashplayer and totem shows about 45 shared libraries but that doesn't really narrow it down much..

any ideas?

---

### Post by mpp on 2010-11-10
Hello,

I have seen similar problems on my P4 with an nvidia mx400 card and (dell) sound blaster live sound card.

I read in this thread [http://ubuntuforums.org/showthread.php?t=1605401&highlight=video+double+speed&page=2](http://ubuntuforums.org/showthread.php?t=1605401&highlight=video+double+speed&page=2) a link to this post [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9961868&postcount=29](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9961868&postcount=29) which seems to have solved the problem for me.

Sometimes VLC is still a bit scratchy - seems to be only at the start of playing a file - but movie player seems to work fine now with videos + music.

You have to edit ```
/etc/pulse/default.pa
``` and find the line with ```
load-module module-udev-detect
``` and edit it to look like this: ```
load-module module-udev-detect tsched=0
``` and reboot.

have fun()
mike

---

### Post by DeSinT on 2012-11-22
Muy Thanks!

This fix also works for Amarok 2.5.0 @ KDE 4.8.5

---

