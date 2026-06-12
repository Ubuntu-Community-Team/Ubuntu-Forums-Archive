---
title: "Bug report : Vlc and ffmpeg conflicts with Sound on 64bit 9.10"
date: 2010-01-31
forum: Multimedia Software
---

### Post by PCA on 2010-01-31
I just upgraded my system to Karmic Koala 64bit version. Initially I just selected all the packages that I had used on my previous Jaunty 32bit, but discovered that the sound wasn't working.

Do I reinstalled and carefully checked certain packages and found that both VLC player and the ffmpeg prevents my sound from playing. The sound settings were shown and everything was normal except for the absence of sound.

I have an HP nx7300. I dunno if this is the right place to post this but atleast someone would know.

---

### Post by PCA on 2010-01-31
There's more... even Avidemux also causes the same problem

---

### Post by PCA on 2010-01-31
I think that I have found the cause of all this trouble..:P It was the Softmodem driver. sl-modem-daemon. After I messed up the second reinstall after getting the updates, I installed everything one at a time to try to replicate the problem.

Everything worked fine including vlc, ffmpeg, avidemux etc.. when I installed sl-modem-daemon the sound system stopped working.

Another thing that I have noticed is that the 64 bit version seems to become slow after certain installation restarts albeit temporarily. A second restart seems to fix it.

---

