---
title: "ATI video threw x11"
date: 2009-03-20
forum: Multimedia Software
---

### Post by Kain000 on 2009-03-20
Hello everyone, I have been trying to help 2 friends geting started with ubuntu 8.10.

they both have ATI cards.   the newer one seems to be working with the fglrx driver fine except when playing video.    we solved this issue in VNC player by routing the video playback threw X11.   this allowed him to keep compiz running while playing video without issue.    

the problem is that this works only for VLC player.   is there a way to put all video (and video such as the music player visuals) threw x11 to solve this problem for good?

---

### Post by markbuntu on 2009-03-20
VLC uses the xine engine so you set that. Totem and others use gstreamer and you can set that to X Window System(No Xv) in System/Preferences/Multimedia Systems Selector/Video.

---

### Post by Kain000 on 2009-03-27
> **markbuntu said:**
> VLC uses the xine engine so you set that. Totem and others use gstreamer and you can set that to X Window System(No Xv) in System/Preferences/Multimedia Systems Selector/Video.

thanks for the response, but I don't see Multimedia systems selector anywhere under system> preferences

---

### Post by markbuntu on 2009-03-27
Then you are missing some gstreamer packages.

---

### Post by Kain000 on 2009-03-27
> **markbuntu said:**
> Then you are missing some gstreamer packages.

any idea witch one would be it?   ive searched synaptic for 'gstreamer' but i get ALOT, and have chosen a few that look promising but I dont just want to install a bunch of packages, wouldnt that hurt my system?

---

### Post by markbuntu on 2009-03-27
No, unless you are extremely limited on disk space. The more gstreamer packages you have the more codecs you get.

---

