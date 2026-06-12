---
title: "Cant play any video file"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by RatonCrispiN on 2007-06-18
hi,  install ubuntu 7.04, install automatix to install codecs, but when i open any file (any format mpg, avi, divx, etc) the mplayer and totem close...

i manage propierties in mplayer (video  x11/xv and codec ffmpeg) but not work closes after open any file, and my cofiguration propierties gone...

---

### Post by fdrake on 2007-06-18
did you activate all your repositories?? [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jerrykun on 2007-06-18
i have the same problem

---

### Post by RatonCrispiN on 2007-06-19
the tuto is for ubuntu 6 and i have 7.04 but i have multiverse,resticted in software sources,

anybody can help me to see videos?

---

### Post by Gremlinzzz on 2007-06-19
uninstall mplayer find it in synaptic and remove it from there.then reinstall  in terminal 
sudo apt-get install mozilla-mplayer
then install these codecs paste in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by RatonCrispiN on 2007-06-19
i try this and post results......thanks for your help

---

### Post by Alex Spencer on 2007-06-19
If that doesn't work, go to Add/Remove Programs and install VLC player...

---

### Post by mpeg2M on 2007-06-19
Another possibility that bit me - Desktop effects seems to interfere with the video players - turn Desktop effects off (if you have it on) & try. Worked for me.

If you're not using desktop effects, then...

   Rich

---

