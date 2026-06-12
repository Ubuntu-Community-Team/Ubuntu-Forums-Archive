---
title: "ZoneMinder question.."
date: 2012-06-11
forum: Multimedia Software
---

### Post by grpace on 2012-06-11
Greetings, all !

I've installed ZoneMinder and I'm having a few issues I don't understand.  I hope someone can shed some light on these things.  I installed it to be a "personal watchdog" with 1 USB webcam connected.  I *hoped* that I could launch it/use it only when I'm away.

1) ZoneMinder Control Panel loads up in Firefox.
2) I can set a "monitor" in the Control Panel.
3) "Probing the camera" fails.

Now, to get to the real matter...

Since I installed ZoneMinder, my webcam is no longer functional under Skype.  From posts I found on the web, I finally managed to get Skype to see the camera successfully with the following command in the launcher:

bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

That worked well until I installed ZoneMinder.

In the Terminal, I can clearly see apache2 and ZoneMinder running as services.

However, when trying to do a "sudo service stop apache2" or a "sudo service stop zoneminder", I get an error stating "Unrecognized service", but I can clearly see them running as services.

I guess my questions boil down to:

1) Is ZoneMinder meant to be run on a stand-alone box...  With nothing else running...  and therefore takes full control ??  If so, then it's not what I was looking for.

2) If #1 above is the case, then how can I disable ZoneMinder when the system is telling me "Unrecognized Service" ??

NOTE: Cheese still sees the camera.  I don't think I've ever gotten guvcview to see the camera (or at least show me a video stream from the cam).  V4L2 Test Bench no longer sees the camera, either (it reports /dev/video0 is "wrapped").

Any help is greatly appreciated.
Thank You.

---

