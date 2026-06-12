---
title: "MJPEG format not working"
date: 2015-01-29
forum: Multimedia Software
---

### Post by guilherme9 on 2015-01-29
Gphoto2 captures live preview frames from cameras and store them as a MJPEG encoded movie.


  For some reason, nothing besides ffmpeg works with it as it should,  all programs just see the first JPG frame (as an still JPG image) and  nothing more. I can convert it through ffmpeg, but this should not be  necessary.

  
I'm trying to use Gstreamer (with gst-launch-0.10) but all options  render the same thing: It only sees the first frame of the MJPEG. 

  
Is this normal? 

  
Is there any way i can configure gphoto2 to use another format, or use ffmpeg to pipeline the decoded frames to gst-launch?

  
Thanks!

---

### Post by Yellow Pasque on 2015-01-29
In my Ubuntu 14.10 VM, gstreamer0.10 plays the mjpeg samples from here just fine: [http://cinelerra-cv.org/footage.php](http://cinelerra-cv.org/footage.php)

Maybe use mediainfo utility to see if there's a difference between some of those files and the ones your camera is making.

---

