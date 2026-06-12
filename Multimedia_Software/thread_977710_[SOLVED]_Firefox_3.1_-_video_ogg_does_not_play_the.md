---
title: "[SOLVED] Firefox 3.1 - video ogg does not play the sound"
date: 2008-11-10
forum: Multimedia Software
---

### Post by abcuser on 2008-11-10
Hi,
on Ubuntu 8.10 I have installed Firefox 3.1 beta 2 nightly build of 2008-11-10 from [Firefox nightly download page](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/).

Firefox 3.1 has one great new feature to play video directly from browser without needing Flash player - so playing video and audio without plugins.

But I am having trouble with audio. Video (pictures) is displayed correctly but there is no sound. On Ubuntu I can play video & audio with movie player and there is no problem, so I don't think there is any kind of problem with drivers.

I have discussed this problem in [Firefox official forum](http://forums.mozillazine.org/viewtopic.php?f=23&t=934055), but all of the people at Firefox forum tested video & audio with Firefox 3.1 on Windows and have no problems. But I would like to test this on Ubuntu not Windows.

Is there any one out there that has tested Firefox 3.1 video and audio?
Can someone confirm if [test web page](http://www.skierpage.com/moz_bugs/test_audio_video_tags.html) is displaying video & audio without problems? Click on link and press button "Play/Pause Video" - do you hear sound? I can hear it for a second and then sound mutes.
Thanks,
Abcuser

---

### Post by abcuser on 2008-12-28
Hi,
today I have downloaded the latest nightly rebuild (see link in previous post) and I have in Help | About the following info: "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2a1pre) Gecko/20081228 Minefield/3.2a1pre"

I have tested <video> and <audio> tag again and now it works fine. It looks like there was some bug and it was fixed.
Regards

---

