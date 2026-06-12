---
title: "padsp doesn't work"
date: 2009-07-07
forum: Multimedia Software
---

### Post by theLured on 2009-07-07
I have searched for ages and I can't seem to get padsp to work. I am on jaunty with everything up to date.
VLC and Audacious both connect to pulse directly and can play sounds together.

I use padsp for wine and gtick(a metronome).
If I have anything running through pulseaudio, I get this error from gtick
/dev/dsp: Device or resource busy

If I close down all programs using pulseaudio, gtick works fine.

I run gtick by
padsp gtick
and the output in preferences are set to /dev/dsp

Also, with gtick running I can't see it listed in pavucontrol > playback and there is no feedback from pavumeter either.
padsp seems to not even attempt to connect to pulse




I'VE SOLVED IT!!! YAY!!!
Okay, I followed this guide as if I was upgrading, so I deleted(and backed up) all my original settings.
I only needed to follow "part A".
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I use XFCE, so In stead of going into System/Preferences/Sound. I went into system/system settings. It's the KDE sound control(command is systemsettings). I think they meant the gnome sound control.
I then went into the Multimedia area and set pulse audio to be the preferred choice on all sections. Click the "prefer" button until pulse goes to the top.
The guide does say that choosing pulse might cause problems. I don't know if it does. I read it after I set everything to pulse.

My sound works fine now. I can run Audacious, VLC, GTick(using padsp) and flash all at the same time.

---

### Post by theLured on 2009-07-08
doesn't anyone know how to solve this?

---

