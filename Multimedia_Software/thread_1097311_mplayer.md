---
title: "mplayer"
date: 2009-03-15
forum: Multimedia Software
---

### Post by rx170 on 2009-03-15
hi installed ubuntu 8.04 mplayer has no color and streaks across the screen.
also the menu buttons won't work for dvd menu.

Thanks:KS

---

### Post by SuperSonic4 on 2009-03-15
Does any other media player (say Totem) have this problem? I'm guessing it's a codec thing. See [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") for adding codecs to ubuntu

---

### Post by kodiakmax on 2009-03-15
Also if you right-click on the file you are trying to play go to properties and the the audio/video tab.  What is the video and audio codec section say?

Is it only one type of file your having problems with? or all files?

---

### Post by rx170 on 2009-03-16
sorry it is totem movie player

---

### Post by rx170 on 2009-03-16
Hi everyone installed vlc media player had the same issue with the color and the lines across the screen.In vlc media player this took care of it:
Changing the video output from "default" or "Xv" to X11 in vlc and smplayer results in perfect video.Still trying to figure it out for totem movie player.

---

### Post by gandaran on 2009-03-17
> **rx170 said:**
> Hi everyone installed vlc media player had the same issue with the color and the lines across the screen.In vlc media player this took care of it:
Changing the video output from "default" or "Xv" to X11 in vlc and smplayer results in perfect video.Still trying to figure it out for totem movie player.
for totem run **gstreamer-properties** in terminal, you can change to x11 there too.

---

### Post by binbash on 2009-03-17
for dvd menus at mplayer you need libdvdnav package.BUt i suggest playing dvd movies with vlc

---

### Post by 3rdalbum on 2009-03-17
For GMplayer, there is a similar option in the preferences panel.

I assume you're using Nvidia proprietary drivers. The drivers that Ubuntu 8.04 can install are quite old and are known to have this video playback problem. However, the new Nvidia 180.xx driver appears to have fixed the problem for everyone.

If you don't mind turning off your graphical system and dropping to a command-prompt, you can install the Nvidia driver from [www.nvidia.com](www.nvidia.com) to fix the problem rather than work-around it.

---

### Post by rx170 on 2009-03-17
Ran VLC media player again and changing the "Xv" to X11 didn't work.I then changed under Video=>Deinterlace=>uncheck disable to Blend thought I had to share that.
Thanks a lot for the responses

---

