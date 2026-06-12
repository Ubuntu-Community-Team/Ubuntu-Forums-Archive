---
title: "Argh... I hate ATI (black screen)"
date: 2009-04-04
forum: Multimedia Software
---

### Post by FrederickUK on 2009-04-04
Hey all - right... I downloaded and installed the 9.3 catalyst driver to attempt to fix my flickery video problems. I wish I hadn't though as flickery video was bliss compared to what I'm left with now.

I'm running 8.10 AMD64 (or I was) and upon rebooting the system, I'm just left with a black screen. Not only that though - the system is unresponsive, hard locked (keyboard doesn't respond or anything - no num lock flash on pressing the button etc)

I rebooted into recovery mode, root console - did aticonfig --initial -f and rebooted again, still hard lock black screen. I rebooted again into recovery mode, tried "Fix X server" from the menu and it came up, but I had massively corrupted graphics and another hard lock (but I could see the desktop background this time).

I tried the instructions on the "Installing ATI/NVidia drivers not the ubuntu way" and that hasn't worked either. Hard lock, black screen, game over :(

I'm having to type this in Vista at the minute, I feel unclean - please help!!!

My video card is an ATi Radeon x1950x Pro.

Thanks in advance :)

---

### Post by FrederickUK on 2009-04-04
Ok little bit of bump and extra info.

I've done a removal of the ati driver using the ati uninstall script in /usr/share/ati - I reinstalled the 9.3 driver and still came up with a black screen of death.

As the driver still didn't work, I've had a look though some X logs I've found, the /var/log/Xorg.0.log is full of IIs but about half way down there's an EE, which I presume is linked to my problem.

This EE is as follows:

```
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] radeon.o kernel module version is 8.59.2 but version 1.17.0 or newer is needed.
[dri] Disabling DRI.
```

It doesn't seem to make sense... 8.59.2 is obviously newer than 1.17.0 so what gives?

---

### Post by xc3RnbFO8P on 2009-04-04
Read this:
[http://ubuntuforums.org/showthread.php?t=873991]("http://ubuntuforums.org/showthread.php?t=873991")

---

### Post by FrederickUK on 2009-04-04
already read that (googled for the error and that was one of the only meaningful hits), it's not very useful.

basically installing the ati driver has lead to requiring a full system reinstall... that's utterly crap tbh.

Where are the fglrx files that need to be purged, or is it a case of apt-get -purge *fglrx*?

---

