---
title: "Webcamstudio destroys all audio"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Mozenrath on 2010-06-30
Hey guys, let me give you some info first.

I'm actually running Linux Mint 9 x64, but I decided to come here because the Linux Mint forums are down.(heh)  

Pretty much, I got fed up with Pulseaudio causing the sound in Flash videos/animations to be delayed, and after looking for weeks and finding no solution, I decided to dump Pulseaudio and go with Esound.

Everything's gone fine until I decided to try Webcamstudio.  As soon as I run Webcam studio, all audio ceases to work.  This means that any Youtube videos playing in Firefox suddenly become silent, and all system sounds are muted.  The only way to cure it is to close Webcamstudio and then close Firefox.  Then all the sounds come back.

Just as a warning, I'd prefer NOT to reinstall Pulseaudio!  If my Flash videos don't work properly, then I had might as well throw Linux out the window.
EDIT: Of course if someone had a way to fix the 1-second audio delay with Flash videos, I'd be happy to switch back to Pulseaudio. :)

---

### Post by howefield on 2010-06-30
> **Mozenrath said:**
> but I decided to come here because the Linux Mint forums are down.(heh)

You may well get someone here who can help, but have you tried here as well ?

[http://www.ws4gl.org/forums-and-help](http://www.ws4gl.org/forums-and-help)

---

### Post by Mozenrath on 2010-06-30
> **howefield said:**
> You may well get someone here who can help, but have you tried here as well ?

[http://www.ws4gl.org/forums-and-help](http://www.ws4gl.org/forums-and-help)

No, but I guess I could try there too!  I have actually had the same problem with a few other programs such as Kino, but that seems to be rare now and not reproduceable.  But with Webcamstudio, it happens nearly every time.

It seems to me like Esound and Webcamstudio are fighting for ALSA, and when Webcamstudio decides to play audio through ALSA it means that all other sound which goes through Esound is now muted.  Just a theory of mine, and I don't know how to fix it.  The same thing happens with Pulseaudio as well.

EDIT: Then again, the sound for Firefox and system sounds don't seem to come back until I kill Firefox.  So I don't know.

---

### Post by Mozenrath on 2010-06-30
Actually, I've discovered it's happening with other programs too, so it's not just Webcamstudio.  Audacity, as soon as it's loaded, causes all other sound to die.(regardless of whether I've set it to use ALSA or OSS) :(

---

