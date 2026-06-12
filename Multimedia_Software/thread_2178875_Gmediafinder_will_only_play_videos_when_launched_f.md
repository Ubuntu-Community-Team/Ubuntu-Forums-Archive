---
title: "Gmediafinder will only play videos when launched from terminal"
date: 2013-10-05
forum: Multimedia Software
---

### Post by Chuckn2x on 2013-10-05
I have a peculiar, I can play videos fine when I launch Gmediafinder, and sometimes even Minitube from the terminal, but if I just try to click on the icon the program will open, and I'll click on a video, it'll appear to be loading, then the program will close. Anyone else have this problem, or a possible solution to this problem?

---

### Post by Chuckn2x on 2013-10-05
[xcb] Unknown sequence number while processing queue
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
python: ../../src/xcb_io.c:274: poll_for_event: Assertion `!xcb_xlib_threads_sequence_lost' failed.
Aborted

gmediafinder: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

Those are two of the various errors I'm getting, no videos are loading at all now, even with the terminal. Strange...

edit: I deleted some Gstreamer file in the home folder and it now runs fine so far.
edit: and now it's not working again, seems to be very inconsistent.

---

### Post by Chuckn2x on 2013-10-06
I just got tired of messing with it, and installed KDE, which uses the Phonon-VLC backend. Minitube works fine now, but I can't install gmediafinder now due to it's dependency on gstreamer. I'm pretty new to this stuff, how could I install gmediafinder with the Phonon-VLC backend?

---

### Post by Chuckn2x on 2013-10-08
Switched back to Unity with the Phonon-VLC backend installed. Too bad I can't install Gmediafinder because it is dependent upon gmediastreamer, oh well, minitube works for me.

---

### Post by Yellow Pasque on 2013-10-09
> **Chuckn2x said:**
> Switched back to Unity with the Phonon-VLC backend installed. Too bad I can't install Gmediafinder because it is dependent upon gstreamer.

The last time I checked, Unity doesn't use Phonon. Also, why can't you really install gmediafinder? Even if one is running KDE, s/he should be able to install/use gstreamer programs. (Phonon's default backend is gstreamer, so it shouldn't cause conflicts with KDE.)

---

### Post by Chuckn2x on 2013-10-09
KDE uses the phonon-vlc backend, at least in my experience. I looked it up and it seems to be that the issue is with the gstreamer back end. I can install Gmediafinder, but it would reinstall the gstreamer-backend, which I do not want, because the minitube app is working perfectly now with the VLC backend. I'm a bit of a Linux noob, but those are my experiences at least.

Edit: oh and I forgot, I switched back to Unity because it just seemed less glitchy to me than KDE, probably something to do with the AMD drivers I'm running.

---

### Post by Yellow Pasque on 2013-10-09
> I can install Gmediafinder, but it would reinstall the gstreamer-backend
You can have multiple Phonon backends installed and choose whichever one you want in KDE's settings ('systemsettings' command).

---

### Post by Chuckn2x on 2013-10-09
The thing is, I want to use Gmediafinder with the Phonon-VLC backend, and I don't know how, or if it is possible. Also, I don't know how to switch backends using Unity.

---

### Post by Yellow Pasque on 2013-10-09
> I want to use Gmediafinder with the Phonon-VLC backend
gmediafinder doesn't use Phonon, so that doesn't make any sense...

> Also, I don't know how to switch backends using Unity. 
```
systemsettings
```

---

### Post by Chuckn2x on 2013-10-09
Well all this stuff is new to me, so my apologies in anything dumb I may say. So there is nothing I can do to fix the problem, except wait until they update gmediafinder? well short of debugging the program myself, which I am clueless about.

---

### Post by Chuckn2x on 2013-10-16
I know that this is a bit late, but I realized that I was using an outdated Minitube package. Instead of using Minitube-Ubuntu I was using the outdated Minitube.

---

