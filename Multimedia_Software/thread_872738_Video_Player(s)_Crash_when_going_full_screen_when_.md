---
title: "Video Player(s) Crash when going full screen when Flash is open"
date: 2008-07-28
forum: Multimedia Software
---

### Post by alloneword on 2008-07-28
Hello all.

I have run into an issue of all video players crashing when trying to go full screen if Flash is running (in FireFox, haven't tested any other browsers).

Xine is configured to us XV for video.

Tested with flash version 9 and the beta of 10.

Ubuntu 8.04 on i386. Nvidia graphics card using latest drivers.

It looks like flash is locking up a hardware resource, but not sure what.

An example output from xine is ad follows:

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  5643
  Current serial number in output stream:  5644

Same issue with VLC, and MPlayer.

Next step here tomorrow when my house mate wakes up tomorrow is to get him to turn off desktop eye candy stuff, see if it goes away.

Has anyone else seen this?

Thanks, Tim.

---

### Post by raccoonone on 2008-08-15
I'm having the same problem. Is there a bug report for this?

---

