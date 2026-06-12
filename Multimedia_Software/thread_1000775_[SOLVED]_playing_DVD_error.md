---
title: "[SOLVED] playing DVD error"
date: 2008-12-03
forum: Multimedia Software
---

### Post by gilloz on 2008-12-03
Every time I put in a DVD to play, I get the error message window saying, unable to open '512'.  If I look under messages in VLC, it says, No suitable access module for 512.  What is this '512' and how would I get rid of this error message?  Thanks.

---

### Post by gilloz on 2008-12-03
Here's an update.  I actually don't even have to install the DVD.  I just click on the VLC Player in Sound & Video and I get the error mentioned above.  Is there anyone that can help me.  BTW, the DVD will play after I have to close the Error window, when I do install a DVD.

---

### Post by mc4man on 2008-12-03
When vlc starts either not working or acting 'odd' the first thing to try is either going to it's settings and resetting to defaults or just plain deleting it's config file.

In 0.9.x it can be found in home folder -> .config. Just delete the vlc folder.

If you happen to be running 0.9.x in hardy then look in home folder and if you see '.vlc' then delete it. (the old config for 0.8.6

For instance I just built 0.9.8a, it wasn't running correct, deleting the vlc folder in .config solved that.

---

### Post by gilloz on 2008-12-05
Thanks mc4man for your reply.  Actually, I downloaded and printed your Tutorial on the newest version of VLC.  I also found the problem to my error.  The command line under Properties for VLC had "vlc 512 %m" because of a post here for a How To instructions on how to make VLC my default player.  When I changed the command line to just plain "vlc %m", my error window disappeared.  Anyway, thanks for your reply and I will look into this upgrade.

---

### Post by mc4man on 2008-12-05
> VLC had "vlc 512 %m"

That would certainly be a problem.

I think that vlc %f is probably a 'better' launch command, though %m does work.

The 0.9.x versions do have some issues, don't be surprised if things that worked in 0.8.6 don't in 0.9.x.
In particular file -> open directory can range from not working at all to sometimes working. (going the 'other way' is a workaround, ie. right click on a directory ' open with'

Right now I'm trying 0.9.6, 0.9.8a and a 1.0-git version to see if one is better suited to me (they all have some limited 'issues'

If your main use is to playback movies then in some regards 0.8.6 is better

---

