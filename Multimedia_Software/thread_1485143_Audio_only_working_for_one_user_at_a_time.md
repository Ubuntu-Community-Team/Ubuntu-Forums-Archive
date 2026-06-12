---
title: "Audio only working for one user at a time"
date: 2010-05-16
forum: Multimedia Software
---

### Post by lmellor on 2010-05-16
I have a strange thing ocurring with my audio setup on 10.04, everything is set as it was after the installation (I've not messed with it).  When switching users there are no audio devices listed in the sound preferences, the volume control icon displays the --- icon and no apps can output any sound from within that user account.

If I log off the first user and then login as another user there is no problem so it would seem that the sound configuration is only setup for one user at a time, this is the first version of Ubuntu that I have known to suffer from this problem, any ideas?

:confused:

---

### Post by lidex on 2010-05-16
OK, so sound works as one user, but not the other, is that correct?

---

### Post by lmellor on 2010-05-17
Sound works in both profiles but not simultaneously. I shall try to explain a little better...

If user 1 logs in, sound works fine.
If user 2 logs in whilst user 1 is logged in they get no sound.
If user 2 logs in alone, sound works fine.
If user 1 logs in whilst user 2 is logged in they get no sound.

Sound only works for the first user to log in, anyone switching to their profile from there gets no sound unless they log the current user out of their session.

This wasn't the case with karmic or any other previous installations on this machine which has been running since before hardy.

I hope this helps.

---

### Post by lidex on 2010-05-17
OK. Apparently there's a reason for that:
[http://swiss.ubuntuforums.org/showthread.php?t=1417647]("http://swiss.ubuntuforums.org/showthread.php?t=1417647")

---

