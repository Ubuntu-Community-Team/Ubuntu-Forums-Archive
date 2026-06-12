---
title: "audio on a command line system with jwm"
date: 2008-04-23
forum: Multimedia Software
---

### Post by penman242 on 2008-04-23
I like to install a command line system from the alternate cd and then use a simple window manager like jwm.  I was wondering if anyone knows how to get pulse working in a situation like that.

I booted the live DVD and audio does work on my intel imac.  I looked to see what all was installed when I ran:

```
sudo aptitude search pulseaudio
```

Which gave:
gstreamer0.10-pulseaudio
pulsaudio
pulsaudio-esound-compat
pulsaudio-module-gconf
pulsaudio-module-hal
pulsaudio-module-x11
pulsaudio-utils

I installed all that and exaile and all its dependencies but still no sound.  Thanks.

---

### Post by justin whitaker on 2008-04-23
> **penman242 said:**
> I like to install a command line system from the alternate cd and then use a simple window manager like jwm.  I was wondering if anyone knows how to get pulse working in a situation like that.

I booted the live DVD and audio does work on my intel imac.  I looked to see what all was installed when I ran:

```
sudo aptitude search pulseaudio
```

Which gave:
gstreamer0.10-pulseaudio
pulsaudio
pulsaudio-esound-compat
pulsaudio-module-gconf
pulsaudio-module-hal
pulsaudio-module-x11
pulsaudio-utils

I installed all that and exaile and all its dependencies but still no sound.  Thanks.

Did you start the daemon?

[http://pulseaudio.org/wiki/FirstSteps](http://pulseaudio.org/wiki/FirstSteps)

---

