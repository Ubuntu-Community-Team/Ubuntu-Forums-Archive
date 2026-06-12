---
title: "Webcam not recognized"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Em_ on 2010-01-04
Hello world,

I'm new to Ubuntu and just installed it on my HP Pavilion, which I also use to run Vista. I've been having issues with the built-in webcam. Initially, Skype recognized the webcam but for some reason I couldn't make video calls. Now, Skype doesn't detect any webcam, nor does Facebook video or Cheese. The built-in microphone works just fine. I'm using Ubuntu 9.10.

Any help would be greatly appreciated!

Em

---

### Post by gradinaruvasile on 2010-01-04
Press alt+f2, type in:

gstreamer-properties

Go to the video tab, select pc camera (or whatever is available as "Device" besides "Default"), press Test. May involve changing the input plugin from "Video for Linux" to "Video for Linux 2", but the camera should be available under video for linux 2.  
If its working, the webcam is configured by the system correctly.


For Skype, first make sure you are using the latest version (2.1.0.47, available on the Skype site), then try the following:
Open a terminal and launch skype by typing (copy-paste):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and press enter. See if you can test the webcam from Skype's Options.

---

### Post by Em_ on 2010-01-04
There isn't any camera available under "Video for Linux 2", so when I hit the test button I get the error message: "Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing."

---

### Post by gradinaruvasile on 2010-01-04
Open a terminal and type:

ls -al /dev/video0

Is there a device?

---

### Post by Em_ on 2010-01-05
When I type that in, I get the following:

crw-rw----+ 1 root video 81, 0 2010-01-04 13:29 /dev/video0

I'm not qiute sure what that means.

---

