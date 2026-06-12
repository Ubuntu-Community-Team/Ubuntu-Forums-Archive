---
title: "Audacious functionaing abnormally"
date: 2008-11-06
forum: Multimedia Software
---

### Post by thomasyen on 2008-11-06
Hello.
Recently I found that whenever I right-click on an mp3 file to open it with Audacious, it would keep playing from the same playlist file (the one I chose the last time I selected from Audacious' file selector) instead of creating a new playlist containing the file I want to play and playing from that. I already tried reinstalling, but the problem persisted. I'm currently using an Intrepid fresh install. Could it be that the Intrepid repository version of Audacious has problems? Any and all help is appreciated. Thank you in advance.

---

### Post by saxonjf on 2008-11-06
I am having the same problem.  There's a patch here, but I don't know how to run a patch.  So if you can run it, you can let me know how to patch it myself.

[http://viewcvs.gentoo.org/viewcvs.py/gentoo-x86/media-sound/audacious/files/1.5.1-commandline-options.patch?rev=1.1&view=markup"]http://viewcvs.gentoo.org/viewcvs.py/gentoo-x86/media-sound/audacious/files/1.5.1-commandline-options.patch?rev=1.1&view=markup](http://viewcvs.gentoo.org/viewcvs.py/gentoo-x86/media-sound/audacious/files/1.5.1-commandline-options.patch?rev=1.1&view=markup"]http://viewcvs.gentoo.org/viewcvs.py/gentoo-x86/media-sound/audacious/files/1.5.1-commandline-options.patch?rev=1.1&view=markup)

---

### Post by thomasyen on 2008-11-08
I read about the patch command (my first ever patching experience too) in the online manual, ran the patch command (I saved the text to audacious.patch in my home folder and used the -b (backup original executable) switch), and got this:
```
thomasyen@thomasyen-desktop:~$ sudo patch -b /usr/bin/audacious audacious.patch
(Stripping trailing CRs from patch.)
patching file /usr/bin/audacious
Hunk #1 FAILED at 315.
Hunk #2 FAILED at 430.
Hunk #3 FAILED at 715.
Hunk #4 FAILED at 734.
4 out of 4 hunks FAILED -- saving rejects to file /usr/bin/audacious.rej
```
The patch attempt was unsuccessful, but I don't know what went wrong. Perhaps someone can explain this to me?

---

### Post by thomasyen on 2008-11-09
I understand what's going on now. This is a patch for Audacious' main.c source code. I installed from a precompiled binary, so it's not much use to me. Thanks anyway. I'll just switch back to XMMS.

---

