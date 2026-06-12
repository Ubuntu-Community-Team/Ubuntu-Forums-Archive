---
title: "how to fix pulseaudio under KDE?"
date: 2009-04-30
forum: Multimedia Software
---

### Post by ejtttje on 2009-04-30
My sound works in Gnome, and I wanted to try KDE, so I did sudo apt-get install kubuntu-desktop, and my wife is quite happy with the environment.  However, sound is not working.  Apparently a lot of people are having trouble with pulseaudio under KDE... how did this get out the door?

Anyway, the common solution is to purge pulseaudio, but the Gnome side still depends on it, and I'd like to be able to switch back and forth.

Audio still works when I use Gnome, but under KDE nothing happens.  It sees the hardware, seems to pretend to be working, but nothing comes out.  I've tried maxing out the volume, and using alsamixer to unmute things.  The only clues to errors I see are when I use System Settings : Multimedia, and press "test" for my  sound card (Intel ICH6), it says something to the effect of not working and falling back to PulseAudio.  If I select PulseAudio and press test, nothing happens.

On /var/log/syslog, I see:
```
Apr 30 20:02:16 midnightsun pulseaudio[4799]: module-x11-xsmp.c: Failed to open connection to session manager: Could not open network socket
Apr 30 20:02:16 midnightsun pulseaudio[4799]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

Thoughts?  Thanks!

---

### Post by Arup on 2009-04-30
KDE doesn't use PULSE, you need to remove PULSE from your system.

---

### Post by ejtttje on 2009-05-01
As stated above, I also have a Gnome installation I'd like to keep, so I'd prefer to know how to fix the configuration so KDE will ignore pulseaudio instead of uninstalling it (and therefore Gnome)

---

### Post by markbuntu on 2009-05-01
To use pulse with KDE4 read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

