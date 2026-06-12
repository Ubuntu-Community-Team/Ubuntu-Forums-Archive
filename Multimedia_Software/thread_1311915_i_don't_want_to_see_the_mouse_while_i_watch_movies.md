---
title: "i don't want to see the mouse while i watch movies with SMPLAYER"
date: 2009-11-02
forum: Multimedia Software
---

### Post by jfca283 on 2009-11-02
hi
i use ubuntu 9.10 as HTPC
i watch mkv files
everything is fine...but
it annoys me seeing the mouse every 5-8 minutes blinking
can i disable it that?
i even disconnect the mouse ( it's a USB one)...but the problem still remains
any idea?
thanks;)

---

### Post by mc4man on 2009-11-02
This is just a guess, maybe the 'Disable_screensaver' option...?

---

### Post by jfca283 on 2009-11-02
i'll try
but i don't think so
because i've never have experience problems with the screensaver
it's the damned cursor blinking...

---

### Post by ikacer on 2009-11-02
I had this happen when I first installed karmic. It doesn't happen any more for me, but I installed so many packages and made so many changes around that time that I'm not sure what actually fixed it.

One thing you might try is changing the sound driver from ALSA to pulse, because I know there were some issues with mplayer and alsa on karmic.

Edit:

Also make sure your SMPlayer and MPlayer versions are up to date. There are two PPAs maintained at this link which you should add if you haven't already:
[http://smplayer.sourceforge.net/downloads.php?tr_lang=en]("http://smplayer.sourceforge.net/downloads.php?tr_lang=en")

---

### Post by jfca283 on 2009-11-02
i'm not sure if i understood well
you mean that changing Alsa to Pulse on Audio Section for mplayer will avoid the blinking problem of the cursor?
i watch and listen the movies well...it's the blinking mouse what annoys me...
thanks for your interest

---

### Post by ikacer on 2009-11-02
Well I just mentioned it because it's the only change I've done to the SMPlayer settings and I think that my curser stopped blinking at the same time I made that change.

---

### Post by rvm4000 on 2009-11-02
> **jfca283 said:**
> hi
i use ubuntu 9.10 as HTPC
i watch mkv files
everything is fine...but
it annoys me seeing the mouse every 5-8 minutes blinking
can i disable it that?
i even disconnect the mouse ( it's a USB one)...but the problem still remains
any idea?
thanks;)

I guess it may be the problem reported here:
[A mouse pointer keeps reappearing during video playback in smplayer](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/455073)

Quick workaround: turn off the "Disable screensaver" option in Preferences -> General -> Video.

---

### Post by jfca283 on 2009-11-04
thanks mc4man...it worked!!!
SOLVED

---

### Post by Stason on 2010-02-24
Menu (or right click) ==> Video ==> Stay on top ==> While playing


This would hide the pointer, which pops up when the "disable screensaver" script moves the mouse every now and then.

---

