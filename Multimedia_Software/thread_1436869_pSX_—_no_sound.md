---
title: "pSX — no sound"
date: 2010-03-23
forum: Multimedia Software
---

### Post by rafe101 on 2010-03-23
I am trying to run pSX on my Myth box (Xubuntu Karmic). At first, it wouldn't run at all. It was seg. faulting. I did what Grishka suggested in this post: [http://ubuntuforums.org/showthread.php?p=7202241](http://ubuntuforums.org/showthread.php?p=7202241)
That got it working, but I have no sound from the application.

As a note, before changing the device ID like he said, I could run pSX with sudo, but I didn't have audio then either.

---

### Post by RedSingularity on 2010-03-23
Do you have audio in other applications?

---

### Post by rafe101 on 2010-03-24
Yeah, the sound works fine in everything else. I think it's related to the pulseaudio problem that seems to cause crashes with pSX for some people (me included). I got it to work by running it with sudo, changing the audio device from "default" and copying the resulting numbers from the root's psx.ini file to the standard user's. But, while it does run now, there's no sound.

---

### Post by RedSingularity on 2010-03-24
You could try removing pulseaudio and see if that solves it.

---

### Post by rafe101 on 2010-03-24
I was thinking of doing that, but I don't really know if it would affect MythTV. Do you know anything about that?

---

### Post by RedSingularity on 2010-03-24
It shouldnt effect anything except that package.

Use the following command

sudo apt-get remove pulseaudio

---

### Post by rafe101 on 2010-03-25
I meant if MythTV used pulseaudio. I suppose I could just put it back if it did.

---

### Post by RedSingularity on 2010-03-25
Pulseaudio is a sound server that allows hardware mixing capabilities.  ALSA is really what the system needs for sound.  And yes you can put it back on later.

---

### Post by rafe101 on 2010-03-29
Removing pulseaudio and setting the sound device back to "default" works.

---

