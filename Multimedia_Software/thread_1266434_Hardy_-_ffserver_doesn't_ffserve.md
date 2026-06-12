---
title: "Hardy - ffserver doesn't ffserve"
date: 2009-09-14
forum: Multimedia Software
---

### Post by ran_talbott on 2009-09-14
I have Hardy installed with ffmpeg version 3:0.cvs20070307-5ubuntu7.3+medibuntu1

I want to stream an analog video capture from a bt878 board in .FLV format (because it will go to Windoze boxes used by people who don't want to install special codecs).

ffmpeg captures the video to a file just fine.  

I had problems getting it working with ffserver,  so I copied the steps and config file in this thread:  [http://ubuntuforums.org/showthread.php?t=665607]("http://ubuntuforums.org/showthread.php?t=665607") to make sure it wasn't my fault.

But that didn't change things:  ffmpeg *says* it's connecting to ffserver and sending data.  But when I try to watch the stream through Firefox,  the Flash player just sits there with its "buffering" display (the "daisy" thingy that replaces the big "play" arrow in the middle of the window).

If I try to fetch test1.flv or test1.swf with wget,  all I get is some header data (187 or 22 bytes,  respectively).  When I tried using MPEG earlier (with a different ffserver.conf file),  wget got 0 bytes of data.

So it appears that ffserver is just swallowing the video data,  and not sending any of it to the clients.

Is this a bug in that particular version?  I'm going to try setting up a jaunty box tonight to get the more recent ffserver,  but I'd like to avoid upgrading my main system just for this bug if I can.

Thanks,

Ran

---

