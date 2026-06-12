---
title: "watch/record video device with no channels in Myth 8.10?"
date: 2009-01-30
forum: Mythbuntu
---

### Post by mathog on 2009-01-30
There is an analog video capture device in my system.  I have verified that it works with VLC, and Mythtv sees it as a capture card too.  It shows up as:

  V4L : /dev/video0

and is an SAA7130 NTSC TV card, configured to take its input from composite.  However, there seems to be no way in Mythtv to use it as a source in "Watch TV", as it has no channel.  Similarly, lacking a channel, it cannot be recorded (for conversion to a digital format.)  Is there some way to assign a "fake" channel to it, so that it can be treated like any other source?  The system also uses the two tuners from an HDHomeRun.

Thanks.

---

### Post by Senkoboy on 2009-01-30
Create a dummy channel.  I did this to record from composite in on my pvr 150.

[http://ubuntuforums.org/showthread.php?t=1031632](http://ubuntuforums.org/showthread.php?t=1031632)

---

