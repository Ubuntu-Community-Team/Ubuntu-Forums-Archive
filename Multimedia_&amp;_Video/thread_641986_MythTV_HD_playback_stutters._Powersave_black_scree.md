---
title: "MythTV: HD playback stutters. Powersave black screen. Related?"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by NT4usB on 2007-12-16
So, after upgrading to 0.20.2 (trying to fix it "the windows way"...) still had HD playback hiccup at ~ one second intervals. Audio and video would pause for an instant, then resume.
Made watching HD recordings impossible.
Strange thing was, restarting the master would fix it for the night. HD played fine. Next day, it would be jacked again.
Tried restarting Myth, gdm, etc. Nothing short of a reboot fixed it.

Also trying to figure out why the screen goes black when sitting on a menu or paused for 10 minutes or so.
Disabling screensaver and powersave in the gui didn't prevent it. Still get a black screen when paused or idle.

Anyway, I'm posting this because although I haven't found the root cause, I have a workaround.
If I kill the processes for gnome-screensaver and gnome-power-manager right after I reboot, no more black screens and no more stuttering.
If I forget and wait until the next day, I get the stuttering. Then, if I kill the processes the stuttering doesn't go away... Have to restart.

Frontend has been up 30 days now without a restart and with good HD playback.

---

