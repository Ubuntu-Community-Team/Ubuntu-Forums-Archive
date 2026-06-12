---
title: "mplayer slow to load, nvidia fx5200"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by garion on 2007-06-26
I recently put Feisty on an old desktop with nvidia fx5200 video.  I installed mplayer from medibuntu.  For some reason the player takes a while ~10 secs to load, and another 10 secs to open any video file, and during that time no cpu or hdd load was observed.  I was using the standard nvidia-glx driver from repo, and I also tried the new driver with envy, same thing.  Playback is fine, no lag, nothing abnormal at all, just the loading of the player itself and everytime when a new file is loaded.  Xine-ui and totem both work well with no problem.  Does anyone know what went wrong here?  Thanks!

---

### Post by Peter Sommer-Larsen on 2007-06-26
I have the same problem - though it is in Edgy with a Ati card

---

### Post by garion on 2007-06-27
any idea how this can be solved?  thanks :)


> **Peter Sommer-Larsen said:**
> I have the same problem - though it is in Edgy with a Ati card

---

### Post by Peter Sommer-Larsen on 2007-06-27
I have no idea - I have started using VLC, which is a same since Mplayer is so much
better.

---

### Post by sagara on 2007-07-25
I am also looking for a solution for this...

---

### Post by sagara on 2007-07-25
I believe I found the problem, this might be the case for you as well.

Open mplayer and open the preferences window.  Under the **misc** tab** uncheck** the option **Stop XScreenSaver**.  This fixed the slow loading for me.  Now mplayer loads inmediately.

---

### Post by wrecche on 2008-04-29
> **sagara said:**
> I believe I found the problem, this might be the case for you as well.

Open mplayer and open the preferences window.  Under the **misc** tab** uncheck** the option **Stop XScreenSaver**.  This fixed the slow loading for me.  Now mplayer loads inmediately.

Zing !  Sorry to bump, but that worked perfectly.

Thanks !

---

