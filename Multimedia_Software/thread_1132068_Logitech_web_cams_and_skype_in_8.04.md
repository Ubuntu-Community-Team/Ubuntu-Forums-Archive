---
title: "Logitech web cams and skype in 8.04"
date: 2009-04-21
forum: Multimedia Software
---

### Post by millspaw on 2009-04-21
I have been fooling around with two Logitech web cams:Logitech Quickcam Express Plus (046d:092f), and a Logitech Labtec Webcam Pro (046d:08a2)

Both worked with Kopete, Ekiga, etc., but would not display a video in Skype's 'Options, Video Source, Test'.  Always just returned a blank screen.

I tried many things over the past 2 weeks, blacklisting ZC3xx, installing Libv4l from 8.10, writing a shell script to pre-load 'v4l1compat.so' before launching skype, and nothing would make Skype return a test video.  It recognized the camera correctly, but just returned a black screen in the test window.

Finally, I just 'skyped' a friend in Florida using the original settings for everything, and VOILA!, IT WORKS.

Apparently the only thing not working is Skype's video test module.  Once the call was initiated, everything worked fine.  Wasted 2 weeks on something that was probably working from the get-go!

---

### Post by mcscratch on 2009-10-21
found the same w/ skype 2.1 beta.  the test video function wasn't working.  couldn't resolve it.  but tested a call over skype, and the video worked perfectly.  so there's an error in the test video section.

---

### Post by Jbike on 2009-11-26
Thank you so much. You have just saved me the same two weeks. I found the problem last night, and worked on on for only about 10 min this morning before I found this post.

Thankyou!

Jbike

---

