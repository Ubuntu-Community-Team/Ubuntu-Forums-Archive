---
title: "XUbuntu install...vx2255wmb claims 1600x1200"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by gpenguin on 2007-07-27
I just bought a Viewsonic VX2255wmb which claims max resultion 1680x1050.  During the XUbuntu install, I went to the monitor's OSD and selected 'Information'.  It claims it is at 1600x1200!  

Has anyone else run into this?  I realize a wide screen monitor is optimum at 1680x1050, which I have yet to read solutions as to how to get.  But I was under the impression 1600x1200 wasn't even possible.

I know, this sounds like question for Viewsonic...I have asked them as well and am waiting for a reply.  I'm just looking to see if anyone else got the same result.

--gpenguin

---

### Post by bandoba on 2007-08-05
Hello, I tried it with XUbuntu but unfortunately, I couldn't even get 1680x1050. 

But now I am using it with Ubuntu and I have set it to 1680x1050 and it runs fine. I am not able to use built-in webcam though. Let me know if you got it running.

---

### Post by eeried on 2007-12-18
Hello,

Coming very late in the thread still the screen is still on sale in my part of the world.

This is a screen I might buy, and I'm interested in your experience.

Glad to see the resolution is fine with ubuntu.

on Xubuntu: check if ou video card is able to display such a resolution. then edit Xorg.conf and add the resoution you want (and remove the one you don't want. restart x (or reboot, that's the lazy solution) and see what happens.

As for the webcam: install a driver (search the web, I caught a glimpse of it) and have a go with Ekiga (choose V4l2). hopefully it'll work...

---

### Post by gubemton on 2007-12-30
Just bought this screen. Very nice, bright, and practical (you can adjust the height and rotate the screen to the left or to the right very easily).

No problem getting Ubuntu to run it at 1680x1050 : you just need to ```

sudo dpkg-reconfigure xserver-xorg
```. I'm pretty sure it'll work whatever your version of Ubuntu is (Kubuntu/Xubuntu...)

I also managed to get the webcam working. I had to recompile the driver from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) as the one in the default install didn't work properly (I'm running Gutsy though).
Unfortunately, of all the applications I've tested, only Ekiga managed to show a picture : Kopete only shows a blank screen, mplayer screams when it tries to capture the cam (there seems to be a patch though), and luvcview (a test app for the driver) only shows a nice black screen.

As I said I'm running Gutsy, with old versions of some apps, so YMMV. Hope it helps anyway.

---

