---
title: "Firewire (1394) Camera not found"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by Pocket Aces on 2007-04-15
I have a simple application running under Suse using a Firewire fire-i webcam.  The application uses opencv to grab frames.  I have libraw1394 and libdc installed, as well as all the opencv libraries/includes.  My application compiles and runs fine so it is finding all the libraries.  /dev/raw1394 is created on startup so at some capacity the system is finding the webcam.

However, when I go to load the camera, in opencv the function call is 
CvCapture* camera = cvCaptureFromCAM(0);

it does not find the camera.  Everything should be essentially the same as the suse machine where this code works. 

More information, when running I now get this:
(dc1394_capture.c) unable to open video1394 device camera 0
dc1394_capture.c: No such file or directory

and running xawtv -hwscan yields:
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
looking for available devices
port 73- 73
   type  :  Xvideo, image scaler
   name : Intel(R) Video Overlay

Any ideas, comments, guides, would be greatly appreciated.

---

### Post by Pocket Aces on 2007-04-15
More information:

If I pass an incorrect parameter to cvCaptureFromCAM (ie, any number other than 0) I just get no camera found with no error message.  Its only when I call it with 0 as the parameter that the "unable to open video1394 device camera 0" occurs.

---

### Post by jiapei100 on 2007-12-13
Exactly the same issue.

Did u sort it out already?

How could u manage to grab the images from 1394 webcam in Linux by using OpenCV?

Regards

---

