---
title: "firefox flash query"
date: 2010-06-20
forum: Multimedia Software
---

### Post by zapstrap on 2010-06-20
I have mythbuntu 10.04 (using the xfce window manager), and periodically use firefox to view flash videos.  I am also running xscreensaver.  Yes, this is a nother how-do-i-disable-screensaver-during-flash-playback post.  

One of the problems with watching flash videos is the screensaver comes on during playback.  I have a script running as a daemon to periodically issue a disable command to xscreensaver if the flash plugin library is resident.  This works great, but I find it's a little ham-fisted.

If I pause playback, the screensaver should still be able to come on, so what I would really like is for the screensaver to be disabled _only_ when flash is actually playing.  Is there a way to query the status of the flash plugin to find out what it's doing so I can be a little more sophisticated about preventing the screensaver from coming on?

---

