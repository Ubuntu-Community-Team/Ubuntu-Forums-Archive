---
title: "Avi, mpeg and DVD's have terrible color after upgrade to 11.1"
date: 2011-10-18
forum: Multimedia Software
---

### Post by bigfootnmd on 2011-10-18
Hi,

I upgraded from 11.04 to 11.10. Movie files, .avi mpeg4 etc.  all have 1960's era colors.  I have removed and reinstalled the Ubuntu restricted extras.  This happens every time I change Ubuntu versions.  So, what do I need to do to get the colors in video files and DVD's back?  Bad playback happens with the media player and vlc.


Thanks

SOLUTION

Google found this link

Fix Blue tinted video in Ubuntu

[http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)

This solution worked.

Make a change to gstreamer-properties.

Open gstreamer-properties from within a terminal.

$ gstreamer-properties

Now click on the Video tab. From the Plugin dropdown box select Custom. Finally add the following line to the Pipeline box.

videobalance hue=-1 ! autovideosink

---

