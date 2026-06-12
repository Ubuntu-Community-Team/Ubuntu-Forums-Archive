---
title: "Removing gspca-source and restoring old gspca driver"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by nelio2k on 2008-01-04
I have a random USB Webcam (Lemel). It worked pretty well under plug and play, and under Ubuntu's Hardware Information it showed up as a video device (/dev/video0).

It also worked under camorama, a program that can take pics with the webcam.

However, I was trying to find a way to make it brighter under Skype, so I saw that the driver in Hardware Information shows gspca as the driver. So I googled and found this gspca-source.

[http://packages.debian.org/unstable/graphics/gspca-source](http://packages.debian.org/unstable/graphics/gspca-source)

So I make and make install, and after a restart Ithink the webcam now doesn't work anymore. Camorama doesn't see the /dev/video0, even when I get results on screen when I run 
cat /dev/video0 and wave my hands in front of the camera. 

On skype, the video now is green. Ican see things but the whole screen is green.

How can I get my old gspca driver back, and undo what this gspca-source has done?
So, pretty much restore the old driver from the kernel, instead of using this new gspca.

Thank you!

---

