---
title: "Problems with Skype and Logitech Quickcam Chat"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Aukikco on 2009-01-24
Ok, so I bought a Logitech Quickcam Chat today. At first I couldn't get it to work at all in Skype, getting just the green screen with noise when clicking the Test button. This has been covered in several threads already.

Eventually, after installing this and that (of which I don't remember all anymore) I finally got the camera working in the test screen by starting Skype from Terminal with the line 
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

However, I cannot seem to find any place to start sending the video when I'm having a chat. 

Also, the picture quality is very blurry. Initially it was also too dark, so I tweaked a bit with XawTV.
Any help?

---

### Post by agarzon on 2009-03-01
I am commenting just to BUMP your thread as I am having the same problem.

The camera used to work in 7.10 out of the box, but there is something in 8.10 that makes it crash.

---

### Post by sa-mejia on 2010-01-24
Bump.

Sort of the same problem here (Although: 1. I am using jaunty  2. The problem does not show up when i test the webcam through skype, but the people to whom I talk complain of the colors being odd).

Santiago

---

### Post by chaanakya_chiraag on 2010-08-15
If skype recognizes you have a webcam, it should have a little blue circle with a video camera icon on it. If you click on it, you will get an option to start sending video

---

