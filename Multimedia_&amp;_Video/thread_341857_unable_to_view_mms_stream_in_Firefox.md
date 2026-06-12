---
title: "unable to view mms stream in Firefox"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by redqueen on 2007-01-19
I can not view mms stream in Firefox such as video stream in cnn.com

Only this message showed in the video screen

"Playing mms://wmscnn.stream.aol........wmv"

The following methods do not help.

1.) I have removed totem-mozilla and reinstalled mplayer 

reference:
[http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html](http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html)

2.) Set about:config in Firefox as following

network.protocol-handler.app.mms user set string /usr/bin/X11/mplayer
network.protocol-handler.external.mms user set boolean true

network.protocol-handler.app.rtsp user set /usr/bin/X11/realplay
network.protocol-handler.external.rtsp user set boolean true

reference: [http://www.ubuntuforums.org/showthread.php?t=114309&highlight=firefox+mms](http://www.ubuntuforums.org/showthread.php?t=114309&highlight=firefox+mms)

---

### Post by DeadEyes on 2007-01-19
As a work around
Copy n Paste the url into a new window and replace mms with http

---

### Post by redqueen on 2007-01-19
Thanks DeadEyes

I just installed MediaPlayerConnectivity from Firefox extension, and configured Windows Media to run with /usr/bin/X11/mplayer . It's work.

So after I copy and paste the link, it needs to go under the MediaPlayerConnectivity and that is also work.

---

