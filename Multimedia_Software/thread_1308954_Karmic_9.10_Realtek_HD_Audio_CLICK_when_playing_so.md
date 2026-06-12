---
title: "Karmic 9.10 Realtek HD Audio CLICK when playing sounds"
date: 2009-11-01
forum: Multimedia Software
---

### Post by davidhoenig on 2009-11-01
I've used 8.04, 8.10, and 9.04 on this hardware without any problems. I just installed 9.10 and love it so far except for one deal-breaker that might make me switch back to 9.04:

Every time a sound is played, whether it be a system sound, music in Rhythmbox, or flashplayer in Firefox, a loud *click* is made right as the sound starts playing. Then the sounds plays fine. The click would be bad enough, but it is LOUD and independent of the volume setting.

My hardware is an ASUS P5K motherboard with on-board Realtek HD Audio (ALC883 I think). Has anyone experienced this, or know what I could try? Thanks!

---

### Post by dbringer on 2009-11-01
I'm getting these clicks too, although not only during playback but every once in a while, especially when adjusting the volume in the mixer. Started after upgrading to 9.10. Otherwise the sound works.

I have a Lenovo Thinkpad with an on-board Intel HD Audio chip (82801H).

---

### Post by Ronald Baljeu on 2009-11-01
Same problem here. My hardware is a Sony Vaio VGN-S3HP with Realtek
audio (ALC260). The click is also heard when changing
the volume settings in the mixer.

---

### Post by willisfang on 2009-11-01
Me 2, (i have posted in another thread though).

whenever I play music, it stops, but music stops, it comes back.
both speaker and jack. I guess it need some signal or something.

---

### Post by Ronald Baljeu on 2009-11-01
Ok, I found a workaround here:
[http://ubuntuforums.org/showthread.php?t=1290222&page=2](http://ubuntuforums.org/showthread.php?t=1290222&page=2)

This works for me.

Just put a hash sign ("#") at the beginning of the last line in
/etc/modprobe.d/alsa-base.conf

---

### Post by davidhoenig on 2009-11-01
Thanks Ronald! This work-around worked for me. Sorry I didn't see that thread in my searching before posting. I'm glad I can stick with Karmic now :). Since a Launchpad bug is already filed for this I am going to mark this thread as solved.

---

