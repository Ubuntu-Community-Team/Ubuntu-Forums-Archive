---
title: "[SOLVED] Cinelerra locks up while playing"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by lledurt on 2008-02-08
Hay all thanks for your help in advance.

My Cinelerra worked great in 7.04 (32) but I have made the jump to 7.10 (64) and I have tried to install it several different ways now and I am getting the same result.

Cinelerra seems stable until I load and play a file.  It works until I stop, pause, or do anything in the play mode, then it locks up and I need to restart Cinelerra.  This happens in the Viewer, Compositor, and Program Windows.  I just noticed that if I delete the audio tracks and work with pure video it works great.  If I add an audio track it freezes when I do anything but play from beginning to end.

All my video files play with mplayer and totem, so it does't seem to be a file problem.  I have tried mp4, mov, mv2, and avi files.  I don't think it is a file issue.

I installed Cinelerra with many methods and my latest has been from source using the following thread [http://ubuntuforums.org/showthread.php?p=4292630#post4292630](http://ubuntuforums.org/showthread.php?p=4292630#post4292630) number 12.  Thanks to cotcot for the  info it is great.

I am sorry for the duplicate post ([http://ubuntuforums.org/showthread.php?p=4292630#post4292630](http://ubuntuforums.org/showthread.php?p=4292630#post4292630)) I thought it was a differen't problem and didn't want to take away from the first poster.

P.J.

---

### Post by lledurt on 2008-02-08
I tried installing the new alsa drivers (alsa-driver-1.0.15 ) thinking that might be it, but that didn't solve my problem in Cinelerra.
P.J.

---

### Post by lledurt on 2008-02-10
This one solved it.

[http://bugs.cinelerra.org/show_bug.cgi?id=426](http://bugs.cinelerra.org/show_bug.cgi?id=426)

I thought I had covered everything also.

**In Preferences>Playback there is a box "Stop Playback Locks Up"**

Selecting this is a workaround and solves my problem.

I will post this on the other thread and make it solved

P.J.

---

