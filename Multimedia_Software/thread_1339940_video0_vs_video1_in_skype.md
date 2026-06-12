---
title: "video0 vs video1 in skype?"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Bogdanovist on 2009-11-28
I have an odd problem with skype and my webcam. When I plug my webcam in, it appears as /dev/video1 and in skype in video devices it also appears in the same place.

However, when I run skype from the command line (in order to see error message) attempts to test or use the video gives the message "Skype Video Capture: Cannot open device '/dev/video0': No such file or directory"

For some reason skype is looking for the webcam in the wrong place (video0 instead of video1) even though the video setting for skype acknowledge it sits at video1. 

Any ideas?

---

### Post by fonkamex on 2009-11-28
Hi,

I had the same problem with my webcam and skype. 

Now, my camera works. I found the solution on skype forums:

[http://forum.skype.com/index.php?showtopic=252681&st=0](http://forum.skype.com/index.php?showtopic=252681&st=0)

Good luck!

---

