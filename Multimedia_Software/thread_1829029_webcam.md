---
title: "webcam"
date: 2011-08-20
forum: Multimedia Software
---

### Post by g8vkv on 2011-08-20
Hi,

I have a Dell 1300 running Kubuntu 11 and attached is a Logitech Pro 9000 webcam.

It works OK - in the sense that Cheese, VLC etc display correctly.

I'm trying to set up video streaming for security monitoring - and because the Dell is pretty slow, I need to stream at a low rate of frames/sec to keep a reasonably low cpu utilisation.

I've tried various things, but the most successful is the motion package, which I can set up with a new frame each second, which is fine.

However, the motion server stops after a seemingly random period with the message ...

[0] Thread 1 - Watchdog timeout, trying to do a graceful restart
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[0] Thread 1 - Watchdog timeout, did NOT restart graceful,killing it!
[0] Calling vid_close() from motion_cleanup
[0] Closing video device /dev/video0

Motion hasn't crashed, it's still running. I also get a message in syslog ...

uvcvideo: Failed to resubmit video URB (-27)

Any ideas of a workaround (other than a cron job to stop/start motion regularly)

g8vkv

---

### Post by no2498 on 2011-08-20
you try zoneminder

[http://www.zoneminder.com/wiki/index.php/Documentation](http://www.zoneminder.com/wiki/index.php/Documentation)

---

### Post by g8vkv on 2011-08-20
> **no2498 said:**
> you try zoneminder

[http://www.zoneminder.com/wiki/index.php/Documentation](http://www.zoneminder.com/wiki/index.php/Documentation)

Thanks for responding.

I used ZM a while ago on a faster Ubuntu box and I had the impression it only works (easily) with video cameras? It also seemed to be pretty cpu-hungry.

My Dell setup is quite slow, but I'm quite keen on using it because a) it only consumes 19W of power - so I can keep it on all the time and b) it lives in an environment where daytime temperatures can hit 40C and it seems quite happy with that.

So I'd really like to try and fix this issue.

---

### Post by no2498 on 2011-08-20
wxcam says it has motion 
ive not tried it myself
you can get it in a deb file look at all files

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

it comes up in sound and video as 
webcam application

---

