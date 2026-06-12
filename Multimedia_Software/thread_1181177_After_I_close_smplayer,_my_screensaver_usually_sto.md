---
title: "After I close smplayer, my screensaver usually stops working."
date: 2009-06-07
forum: Multimedia Software
---

### Post by bobtestact on 2009-06-07
After I close smplayer, my screensaver usually stops working.  (That is, the screensaver no longer automatically activates after 10 minutes of idle.)

Has anyone else encountered this problem with smplayer (or maybe mplayer)?

Does anyone have a simple fix for this problem?

------------------------------------

Detailed info:

I usually run smplayer in full-screen mode.

Within smplayer, the option to "disable screensaver" is enabled.  But I'm assuming that this feature should be in force only while smplayer is actually running.

After the screensaver gets into this "broken" state, I have verified that (1) the "gnome-screensaver" process is still running, (2) no "smplayer" or "mplayer" process is still running, (3) the item to "Activate screensaver when idle" is still enabled in "gnome-screensaver-preferences".  Also, when I run the command "[COLOR=Blue]gnome-screensaver-command --query[/COLOR]", I get:
[COLOR=Green]
The screensaver is inactive
The screensaver is not inhibited[/COLOR]

So I'm not seeing any clues why the screensaver is now in a "broken" state (i.e. now unable to activate after 10 minutes of idle).

The fastest fix I have found so far is to log off after closing smplayer.  I would like to find a better solution.

Ubuntu 9.04 on amd64
smplayer 0.6.7-1~jaunty4
mplayer 1.0~rc3~pre1-0jaunty2

---

### Post by rvm4000 on 2009-06-08
> **bobtestact said:**
> mplayer 1.0~rc3~pre1-0jaunty2

That might happen if mplayer is not closed properly. Anyway that mplayer build contains a patch to support the gnome screensaver. Maybe it's not working properly, maybe I should remove it in the next build...

---

### Post by bobtestact on 2009-06-08
> **rvm4000 said:**
> That might happen if mplayer is not closed properly. Anyway that mplayer build contains a patch to support the gnome screensaver. Maybe it's not working properly, maybe I should remove it in the next build...

Thanks for the info.

Does anyone have a workaround that's less drastic than logging out?  Like maybe a batch file I can run every time I close smplayer that fixes gnome-screensaver?

---

### Post by rvm4000 on 2009-06-09
New build mplayer - 2:1.0~rc3~pre1-0jaunty4, compiled without the gnome-screensaver patch, available at [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

Could you test if that fixes your problem with the screensaver?

---

### Post by bobtestact on 2009-06-09
> **rvm4000 said:**
> New build mplayer - 2:1.0~rc3~pre1-0jaunty4, compiled without the gnome-screensaver patch, available at [https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")

Could you test if that fixes your problem with the screensaver?

With the new version installed:

The screensaver now activates 10 minutes after starting the movie.  In smplayer, the "Disable screensaver" option is enabled.

After closing smplayer, the screensaver now activates as expected after 10 minutes of idle.

--------------------

This is an improvement, as the screensaver does not become "broken" anymore after running smplayer. Unfortunately, the "disable screensaver" option in smplayer is not working anymore, so it would be nice to fix that one eventually.  Until then, I'll wrap my smplayer launcher in a batch file that disables/reenables the screensaver.

Thanks for the fix.

---

### Post by rvm4000 on 2009-06-09
That's normal. See the FAQ:

> 
**21. The screensaver doesn't turn off, why? **

If you use a recent version of MPlayer you may need to add a line like this in your ~/.mplayer/config: 

(gnome) 

heartbeat-cmd="gnome-screensaver-command -p &>/dev/null"

 (kde) 

heartbeat-cmd="dcop kdesktop KScreensaverIface enable false &>/dev/null && dcop kdesktop KScreensaverIface enable true &>/dev/null"


More info:
[http://smplayer.berlios.de/forums/viewtopic.php?id=329](http://smplayer.berlios.de/forums/viewtopic.php?id=329)

---

### Post by bobtestact on 2009-06-09
> **rvm4000 said:**
> That's normal. See the FAQ

Thanks for the tip.  That's even easier than what I had planned to do.

---

