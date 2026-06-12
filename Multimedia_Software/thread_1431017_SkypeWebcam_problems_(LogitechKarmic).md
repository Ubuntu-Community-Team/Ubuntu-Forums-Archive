---
title: "Skype/Webcam problems (Logitech/Karmic)"
date: 2010-03-16
forum: Multimedia Software
---

### Post by Randy Rhinoceros 13.04 on 2010-03-16
I am somewhat new, and I am having problems using my webcam in Skype:

Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000

When I'm in a call and I turn it on Skype immidiately crashes.
(using  LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype does not work):

/usr/local/bin/skype: line 2:  2795 Segmentation fault      /usr/bin/skype

When I use gstreamer-properties I get the following messages but my camera works:

$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

(Note /system/gstreamer/0.10/default/videosink is set to autovideosink)

I'm using 9.10 karmic on an intel system (not sure how to get the a list of specs)
Any help would be awesome, Thanks!
-Randy Rhino

---

### Post by partloer on 2010-03-16
Hi Randy Rhino,

Well according to the Ubuntu's Logitech Webcam Support this should work out of the box.  But I have read that this web camera sometimes needs some work to get it running.
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech")

I would make sure that you have the latest version of Skype 2.1.0.81
[http://www.skype.com/download/skype/linux/choose/]("http://www.skype.com/download/skype/linux/choose/")

I would also read this page to see if this helps
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

However if the above doesn't work I would check out this site and follow the directions and see if you can get it working.
[http://www.noah.org/wiki/Logitech_QuickCam_Pro_4000_on_Ubuntu]("http://www.noah.org/wiki/Logitech_QuickCam_Pro_4000_on_Ubuntu")

Let me know how this goes.

---

### Post by Randy Rhinoceros 13.04 on 2010-03-17
Thanks for the prompt reply and the useful links!  I do have Skype ...81.  I also should mention my Koala is 32-bit which seems to be important. I used the Ubuntu webcam link to test it and found that my computer recognizes the device (and microphone which I finally got working).

I think the webcam itself is working, even in Skype I am able to see myself under options>>video devices or after using the gstreamer-properties command (only I get all those failed plug-in messages in my console). The quality could be a little better (a strange grey appears in brighter spots), but I can live with that. The problem begins when I try to turn my camera on during a phone call, I see it pop up for a split second and then Skype crashes.

---

### Post by Randy Rhinoceros 13.04 on 2010-03-17
Setting the receiving video to double size allows me to start my own video! (as described here):
[http://forum.skype.com/index.php?showtopic=412011](http://forum.skype.com/index.php?showtopic=412011)
Not a fix or the best work around but it works for now...

---

