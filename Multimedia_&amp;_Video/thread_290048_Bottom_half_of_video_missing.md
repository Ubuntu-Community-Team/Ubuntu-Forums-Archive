---
title: "Bottom half of video missing"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by Cranki on 2006-10-31
Hi all,

I upgraded my HTPC from Dapper to Edgy a couple of days ago. It's basically a normal PC (not running myth) except the output is 848x480 to S-Video on an ATi 9600XT.

Since the upgrade, all of my videos (which I think are all xvid or divx) play very strangely. Only the top half of the video is shown, but it is stretched out so that it fills the space that should be taken up by the whole video.

So if the video was in 640x480, I only see the top 320 pixels, but stretched out at double height.

I've tried this in xine-player, mplayer, totem-gstreamer and totem-xine, and have the same problem in each. I've installed the w32codecs package from the edgy-plf repository.

What should my first troubleshooting step be?

Thanks!
Ben.

---

### Post by belly917 on 2006-11-04
well, I don't have a solution for you, but I can tell you what's going on since I have the same problem.

If you use:
**1** the proprietary ATI drivers (fglrx) version 8.21 - 8.30(current)

**2** tv-out (via s-video or composite)

**3** have Video Overlay (Xv) enabled in your /etc/X11/xorg.conf

then all your video will do this.

This makes my mythtv box almost useless since I can't watch anything I record.  If I turn off Video Overlay, the picture looks correct, but it stutters because the cpu can't handle it.  If I hook up my mythtv box to a lcd or crt, the video overlay works correctly.

I have been searching everywhere for a solution, and it took forever before other people with this problem surfaced.  There is another [thread in this forum](http://www.ubuntuforums.org/showthread.php?t=249846) but no-one yet has a solution.

Someone did mention that using fglrx 8.20 doesn't have this problem, but I would think they would be incompatible with the Xorg version included in edgy since the 8.30.3 driver's release notes mention Xorg 7.1 compatibility.

---

### Post by bruceleo on 2007-04-12
In /etc/X11/xorg.conf:
Under "Devices" set Option "VideoOverlay" to "off"

---

