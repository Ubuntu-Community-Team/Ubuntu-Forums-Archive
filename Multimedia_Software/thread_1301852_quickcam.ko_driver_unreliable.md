---
title: "quickcam.ko driver unreliable?"
date: 2009-10-26
forum: Multimedia Software
---

### Post by ran_talbott on 2009-10-26
I have 3 Logitech USB cameras,  One of them (a Quickcam VC,  USB ID 0478:0001) isn't supported by any of the drivers supplied with Hardy,  but does have a driver (qcamvc, sourceforge page [here]("http://sourceforge.net/projects/usb-quickcam-vc/files/")) that I haven't tried yet.

But I have two that *are* supposed to work with the included quickcam.ko driver:  one of the many that Logitech called an "Express" (USB ID 046d:0840),  and one they made for Lego' "Vision Command" set (USB ID 046d:0850).  I'd really like to get the Lego camera working,  but have had nothing but problems with both cameras.

I'm currently running Hardy Server (kernel updated to 2.6.24-23-server) with KDE from Kubuntu installed on top of it.

I tested the "Express" camera with:

camorama:  hangs, process couldn't be killed.  Had to reboot to get rid of it.

cheese: nothing but a "test pattern" display (but I haven't gotten *any* camera to do anything different with cheese,  so that doesn't say much).

kopete: hangs,  but my notes indicate I was able to kill it.

skype: crashed (my notes don't say whether it was just the app or the whole system).

xawtv: crashed (ditto).

I've gotten kopete and xawtv to work with a few other cameras (some USB,  some not),  so I know it's not just a problem with a bad version of the app(s).

Hoping that the problem was that my flea-market-special Express camera was bad,  I hooked up the brand-new Lego cam over the weekend.  The instant xawtv displayed its window,  the whole system locked up hard.  The only hint any code anywhere was still running was the flashing of the Num Lock and Scroll Lock lights on the keyboard.  I couldn't even reset the system with the front panel button:  I had to pull the power cord to restart it.

I had checked the system log before starting xawtv,  and saw that the quickcam driver had connected with the camera,  identified it as having a VV6410 sensor,  and assigned it as /dev/video0.  So I'm pretty sure that the camera is good.

After having really bad experiences with two different cameras,  I'm wondering if the real problem is that the driver (which appears to be no longer actively developed/maintained) is the problem.  Is anyone getting good results using any of the cameras supported by this driver?  If so,  please let me know what system you're running it with:  I'd be willing to consider setting up an old PC as a "Legocam server" with an old version of Linux if it would get the camera working.

Thanks,

Ran

---

