---
title: "Streaming Video"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by marcog42 on 2007-06-04
Hello,

I'm curious about streaming video from my home PC.  I use an XP machine at work and the net connection is firewalled, so I connect via https port through SSH in order to run linux apps on my work PC.  I was wondering if it's possible to stream video as well.  Doesn't have to be great quality.  Just enough to keep me entertained in between taking care of any phone/VM troubles that come up.  I have a pretty fast cable connection at home... 15Mb/s download and 2Mb/s upload, so bandwidth shouldn't be too big an issue.  I've never streamed any sort of content over the internet, just inside my own network, so any pointers would be greatly appreciated!  Thanks!

---

### Post by mohnkern on 2007-06-04
I haven't tried video, but I expect if you installed gnump3d it might be able to do it.  It certainly streams the audio well.

Of course that presumes you have sufficient upstream bandwidth from home to stream.  If you're on a cable connection, it may have a cap on how fast you can upload.

Also, you may need to reconfigure your router to do port forwarding on port 8888 to your machine.

---

### Post by marcog42 on 2007-06-04
My upstream is ~ 2Mb/s so I can upload at around 200 KB/s, and I've seen it go as high as 250 KB/s.  I've tried gnump3d to stream my audio here at work, only I had the server sending on port 443 as the only ports available for me at work are port 88 and 443 (http and https, respectively.)  It worked well, no hiccups, but I can't run gnump3d and my SSH at the same time since that's the only port I can use to be able to connect from work.

---

