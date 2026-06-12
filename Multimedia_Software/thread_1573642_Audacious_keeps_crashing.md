---
title: "Audacious keeps crashing"
date: 2010-09-13
forum: Multimedia Software
---

### Post by Dobbie03 on 2010-09-13
I have a pretty fresh install of Ubuntu with Audacious 2.4 RC2 installed.  For the first few days it ran fine, since Saturday it keeps crashing literally 1-2 seconds after opening it.  Anyone else having this problem?  Anyone know how to fix it?

---

### Post by Dobbie03 on 2010-09-14
Anyone?

---

### Post by Yellow Pasque on 2010-09-14
Start it from the terminal so you might see why it's crashing.

---

### Post by Dobbie03 on 2010-09-16
Ok, I just tried that and this is what came up:


```
(audacious:7216): Gdk-CRITICAL **: IA__gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:7216): Gdk-CRITICAL **: IA__gdk_drawable_get_screen: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:7216): Gdk-CRITICAL **: IA__gdk_drawable_get_depth: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:7216): Gdk-CRITICAL **: IA__gdk_screen_get_rgb_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(audacious:7216): Gdk-CRITICAL **: IA__gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault
```

---

### Post by 4Orbs on 2010-09-16
I think you only need to install a skin on it (find it in Synaptic Pkg Mgr).

---

### Post by Dobbie03 on 2010-09-16
I couldnt find anything in Synaptic that looks like a skin for Audacious.

---

### Post by Dobbie03 on 2010-09-17
Anyone else have any ideas?  I thought Audacious may be conflicting with Emerald but nope, I changed back to normal and Audacious still crashes with the same output from the terminal as above.

---

### Post by Yellow Pasque on 2010-09-17
Try a different version? [https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

### Post by Dobbie03 on 2010-09-17
Nope, that didnt help either.  I think I should just give up.

---

### Post by Dobbie03 on 2010-11-08
OK, this has happened again.  I recently installed Ubuntu 10.10 and Audacious lasted 4 days before it started crashing again.  It has the same output as above as well.
```

(audacious:24459): Gdk-CRITICAL **: IA__gdk_drawable_get_colormap: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:24459): Gdk-CRITICAL **: IA__gdk_drawable_get_screen: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:24459): Gdk-CRITICAL **: IA__gdk_drawable_get_depth: assertion `GDK_IS_DRAWABLE (drawable)' failed

(audacious:24459): Gdk-CRITICAL **: IA__gdk_screen_get_rgb_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(audacious:24459): Gdk-CRITICAL **: IA__gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
Segmentation fault
```

Does anyone have any ideas about this?

---

### Post by cchhrriiss121212 on 2010-11-08
Are you running as root or multiple users?

---

### Post by Yellow Pasque on 2010-11-08
Install the audacious-dbg package so you can get a backtrace and file a bug report.

---

### Post by Dobbie03 on 2010-11-08
> **cchhrriiss121212 said:**
> Are you running as root or multiple users?

As root.

---

### Post by Dobbie03 on 2010-11-08
> **Temüjin said:**
> Install the audacious-dbg package so you can get a backtrace and file a bug report.

Thanks, I have installed that.

---

### Post by cchhrriiss121212 on 2010-11-08
> **MattDobson said:**
> As root.
There's your problem, avoid running any regular program as root as you will get issues like this every time.

---

### Post by Dobbie03 on 2010-11-08
Cool thanks, lets hope this works :)

---

### Post by Dobbie03 on 2010-11-09
I forgot to ask, how do I make Audacious run as all users as opposed to running as Root?

---

### Post by cchhrriiss121212 on 2010-11-09
When you install a new program and start it, you will be doing so as a user. If you were running it as root you would first log in as root in a terminal and then run the program. Using sudo to start a program is also a bad idea. See here for more info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If I were you I would delete the audacious config files (~/.config/audacious) and reinstall the program.

---

### Post by mc4man on 2010-11-09
Depending on how you were running audacious as root you may also wish to look in /root/.config for an audacious folder and remove it. (screen

---

