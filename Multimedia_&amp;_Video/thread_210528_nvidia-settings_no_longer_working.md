---
title: "nvidia-settings no longer working"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by onlysolution on 2006-07-07
I have a GeForce 6800 and a  pentium 4 32-bit system, installed the latest nvidia drivers, played ut2004 flawlessly, and was able to run nvidia-settings fine.  Invigorated by my success, I decided that I was time enough to install xgl and compiz for sweet 3D accelerated desktop action. After installing and rebooting and configuring xgl/compiz I tried to run nvidia-settings again, only to get the following error (regardless of compiz being on or off or having been run previously on my session):
```
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.
```
Yay, that isn't very useful!
OpenGL games still work fine when run with xgame in a seperate x session, but I'd like to try enabling anti-aliasing, etc.  Any ideas?

---

### Post by Athropos on 2006-07-07
Did you try to completely disable Xgl ? Even if Compiz is not running, you may have Xgl running...

---

### Post by onlysolution on 2006-07-07
I know I do not understand the windowing/session model, etc so please forgive if this sounds stupid.  As I understand from the installation and what I have read, etc, I have replaced normal x with xgl as my x server.  Killing xgl would get me a pretty text terminal then, would it not?  How would I go about switching (temporarily) back to normal x?

---

### Post by Athropos on 2006-07-07
It depends on the method you used to start Xgl. Most of the time, you have to edit '/etc/gdm/gdm.conf-custom' and add values to '[servers]' and '[server-Xgl]' sections. You should revert back to the old version, or undo the changes you made. Then, after a restart of gdm, Xgl is not launched anymore.

---

### Post by onlysolution on 2006-07-07
Can't I open another non-gl x-session on a different display, and kill xgl from there (if needed) make my changes, restart xgl move back and kill the other x session?

---

### Post by onlysolution on 2006-07-08
*whump*

---

### Post by RawMustard on 2006-07-09
I don't get the errors you get, but nvidia settings stop working here when I installed XGL/Compiz also.  I can still call it up, but I get no options displayed!

Anyway, not a big issue for me as I never really used it for anything.

---

### Post by onlysolution on 2006-07-09
But don't you want xgl... with anti-aliasing and ansiotropic filtering?! XD
We should ask quinnstorm to add HDR to the next build of compiz!  

But seriously, no ideas?

---

### Post by tseliot on 2006-07-09
Have a look at this thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=66501&highlight=nvidia-settings+XGL](http://www.nvnews.net/vbulletin/showthread.php?t=66501&highlight=nvidia-settings+XGL)

---

### Post by RawMustard on 2006-07-09
> **onlysolution said:**
> But don't you want xgl... with anti-aliasing and ansiotropic filtering?! XD
We should ask quinnstorm to add HDR to the next build of compiz!  

But seriously, no ideas?

sudo gedit /etc/init.d/gdm

look for
```
if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi
```

Change to
```
if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
    export __GL_FSAA_MODE=5
    export __GL_LOG_MAX_ANISO=3
    export __GL_SYNC_TO_VBLANK=1
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi
```

CNTRL ALT BACKSPACE

And you're done :)

---

### Post by onlysolution on 2006-07-09
This looks like a great idea, but near as I can tell, this doesn't wind up exporting these env vars, even when I moved the exports out of the 'if LANG=$(pam_getenv -l LANG); then' if block.  Did I miss something?

---

