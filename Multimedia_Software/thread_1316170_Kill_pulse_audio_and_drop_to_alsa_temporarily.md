---
title: "Kill pulse audio and drop to alsa temporarily"
date: 2009-11-05
forum: Multimedia Software
---

### Post by marshmallow1304 on 2009-11-05
Due to pulseaudio not playing nicely with a couple of games under Karmic, I'd like to temporarily disable it.  I seem to remember that killing pulseaudio in past releases would allow alsa to take over, but now when I kill pulseaudio, I get no sound at all.  Are there packages I need to install to allow alsa to work without PA?

---

### Post by Ulysses361 on 2009-11-06
You could always try the following procedure to replace pulseaudio with esound:

[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)

---

### Post by ted.hallberg on 2009-11-06
> **marshmallow1304 said:**
> Due to pulseaudio not playing nicely with a couple of games under Karmic, I'd like to temporarily disable it.  I seem to remember that killing pulseaudio in past releases would allow alsa to take over, but now when I kill pulseaudio, I get no sound at all.  Are there packages I need to install to allow alsa to work without PA?

You could also try to start your games with the following command "pasuspender *game*". This disables pulseaudio for the process that is executed.

---

### Post by marshmallow1304 on 2009-11-06
> **ted.hallberg said:**
> You could also try to start your games with the following command "pasuspender *game*". This disables pulseaudio for the process that is executed.

I tried that and got no sound at all.

---

### Post by marshmallow1304 on 2009-11-07
Bump.

I did this:
```
sudo apt-get remove pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
sudo reboot
```

and sound works perfectly, but I miss the advanced settings of pulse.  Is there any way to leave pulse installed alongside esound and use esound only for a couple applications?

---

### Post by Claus7 on 2009-11-07
Hello,

I was having both, and after some time sound was gone. I executed the commands you provide rebooted and everything is working nicely. Hope that my sound will keep working no matter what.

Which are the advanced settings you miss so much?

Regards!

---

### Post by marshmallow1304 on 2009-11-07
> **Claus7 said:**
> Which are the advanced settings you miss so much?

The tray icon, being able to turn the volume up to 150%, changing volume by application.  Also, FoFiX refused to start after I removed pulse.

---

### Post by marshmallow1304 on 2009-11-24
This probably deserves a new thread, but I'll bump this one.  I've attached a log of pulseaudio while it goes bad while playing a game.


Edit:
I'm going to mark this thread as solved, even though it technically isn't completely solved.  I figured out how to kill pulse easily without removing it and installing esound, though I would still be interested if anyone knows why pulse behaves so oddly in the first place.

---

### Post by leomeloxp on 2011-03-17
I know this is marked as solved but I got under the same problem and couldn't solve it still.

Thing is, if I remove pulseaudio and call gnome-alsamixer my games and sound work okay, except that I have a bluetooth headset and can't set it up on Alsa. I can't give up pulse same way because it has settings of sound for individual applications wich for me is very useful.

How do you shut pulse down without removing it and use alsa instead?

I don't mind not using my headset for gaming, all I need is a way of killing Pulse and then calling it back in case I need (because alsa can be killed easily). I think maybe gconf-editor can help, but couldn't find anything.

If anyone can give a hand, I'll be happy =]

---

