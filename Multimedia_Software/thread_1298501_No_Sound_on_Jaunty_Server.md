---
title: "No Sound on Jaunty Server"
date: 2009-10-22
forum: Multimedia Software
---

### Post by krakerjak on 2009-10-22
I've just set up a media server running Jaunty Server edition.  It is a headless box that is tucked away in a closet in my office.  Everything works perfect except the sound.  I like to use MPD to listen to music while I'm working in the office or the garage (the speakers are connected to the server).

With the server edition, I don't usually get any sound.  What I mean is sometimes it works, and then I reboot, and then it doesn't.  It's very frustrating.  One thing I've noticed though is that ***aplay -l*** always comes back with no soundcards listed.  On the other hand, ***asoundconfig list*** always returns the sound card that is installed.

I have gone through the [Comprehensive Sound Problem Solution Guide]("http://ubuntuforums.org/showthread.php?t=205449"), and still no luck.  Out of desperation, I downloaded the desktop edition, and booted the computer up in LiveCD mode.  The sound worked, and ***aplay -l*** returned the expected results.

So, all of that background to ask this simple question:  Does anyone know how I can get the sound working on the server edition?  Or should I wipe the drive, and go with the desktop edition (which had it's own set of issues)?  I guess that's two questions. :)

---

### Post by krakerjak on 2009-10-24
Just an update, I threw in another drive, and loaded debian on it just to see what it would do.  After I installed alsa on it, my hardware showed up.  The only thing I can figure is that there is something that gets missed with the server edition that is needed to properly use sound.

Does anyone know if this is the case?

---

### Post by krakerjak on 2009-10-25
Now I have a little more information.  I ended up wiping the drive, and installing the desktop version.  I opened the terminal up and verified that alsa was seeing the soundcard, and it was.  I disabled GDM, and rebooted.  After the reboot, alsa no longer saw the soundcard.  So.... the issue is with GDM.

Can anyone help me with this?  I really want to have sound on this machine.

---

### Post by krakerjak on 2009-10-28
I never have gotten it to work right, so I gave up.  I put debian on it, and we're in good shape.

---

