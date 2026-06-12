---
title: "Miro Crashes at end of playback"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by eosha on 2008-02-28
Miro plays videos just fine, but as soon as the video is finished it segfaults like so:

> WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
Segmentation fault (core dumped)
me@me:~$ TIMING   WARNING: Calling <bound method DownloaderDaemon.closeCallback of <dl_daemon.daemon.DownloaderDaemon object at 0x835afac>> on AsyncSocket: Outgoing 127.0.0.1:59041 too slow (3.489 secs)

It's 100% repeatable... any ideas?

---

### Post by crysys on 2008-02-29
Did you by chance have backports enabled?  You problem is identical to mine and that is a result of the problem in [_this_]("http://ubuntuforums.org/showthread.php?t=708059") thread.

I can tell you what hasn't worked for me.  Rather than try to downgrade libxine1 as suggested in that thread, I downgraded miro-data back to pcf1.  It improved WMV playback 100% but Miro still crashes out at the end of the video.  I have removed the backports repository and I'll be downgrading libxine1 next.

Call me crazy but should miro-data and miro packages be dependent on each other to prevent a half upgrade?

---

