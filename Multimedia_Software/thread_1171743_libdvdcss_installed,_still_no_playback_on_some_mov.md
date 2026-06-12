---
title: "libdvdcss installed, still no playback on some movies"
date: 2009-05-27
forum: Multimedia Software
---

### Post by matthew_petty on 2009-05-27
Hello everyone,

I've followed the directions in the Comprehensive sticky for a fresh Jaunty install, but I'm still having problems with some movies.

totem-xine asks if I'm trying to play encrypted dvd's without libdvdcss, but I know I have it installed. I've tested this on my other Jaunty boxes, and the dvd is decrypted and playback is normal.

Any ideas? What outputs can I give you to help me diagnose this?

---

### Post by Chas_E_Erath on 2009-05-30
> **matthew_petty said:**
> 
Any ideas? What outputs can I give you to help me diagnose this?

============

***  Sorry, I just reread your problem and this stuff might be pointless in light of that fact.  But, wth, I'll leave it anyway ***

Hi,

There's no guarantee that I can help - I'm the type that stumbles around for a long while before the problem gets resolved - but here are some things I try.  In a terminal (ie. xterm):


1.   eject /dev/dvd     (assuming /dev/dvd is correct)

   If that doesn't work (note any errors in the xterm) then:

       sudo eject /dev/dvd

if that doesn't work then I doubt I can help.  If that worked but the first didn't, then its a permissions thing.


2.  sudo tail -f /var/log/messages

  (this will give you a continuous output of any new lines that are written to that log  (ctrl-c to quit))

  Then put the dvd into the drive and close the door.  Watch to see what shows up in that terminal window.  If there are errors, the problem should be revealed, or at least hinted at.


3.  xine (or gmplayer or whatever or totem I suppose (but I've never used that one))

  If you start them from a terminal, then errors will be echoed to stdout (which is the terminal from which you started it).  



These are good, easy places to start.  But like I said, I usually fumble around in the dark until I stub my toe on the problem.

Hope that helps & good luck.
Chas.

---

