---
title: "Logitech Quickcam Pro 9000 does does not work with Adobe Flash in my 10.04"
date: 2010-08-09
forum: Multimedia Software
---

### Post by StewartM on 2010-08-09
Greetings,

I have a Logitech QuickCam Pro 9000 which works with Skype, Cheese, Ekiga, and Flash on Ubuntu 9.10 with no problems. (With Ubuntu 8.04, the video worked with all of these but Skype (couldn't test Skype as it was not available) but not the audio, which was one of the reasons I upgraded).

It does not work with Flash in Ubuntu 10.04. Flash does not detect the camera though it does detect the microphone (and says it works, haven't tested it yet). It works (video and audio) with Skype and Ekiga. The video works with cheese and I can record my own voice with Sound Recorder off the webcam's mic.

I have looked at the webcam community documentation 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

and have visited Adobe's site 

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

to click on "always allow". But that does not work either. Flash simply does not see the camera. The version of flash on both computers is the same (10,1,53,64).

Any suggestions?

StewartM

---

### Post by no2498 on 2010-08-10
the site i go to said the last adobe update they got broke the cam drivers
you said you clicked allow did you click remember also

i use the opera browser btw
if i try firefox it uses the opera flash lib's
so your fix is in firefox

hope this points you the right way

---

### Post by StewartM on 2010-08-12
Well, I removed both flash and firefox this morning (with the --purge switch) and then re-installed both. With flash, there was a new version which installed both on my desktop running 10.04 (where the webcam doesn't work with flash) and the laptop running 9.10 (where it does). I tested both systems, and the webcam continues to work with the laptop and not the desktop even though they run the same version of flash.

I am now wondering if the video card driver could be an issue, as that is clearly a difference between the two computers. On my desktop, when it ran 8.04, it ran the NVIDIA 173 driver for the GeForce 8600 card that came with the system. With the upgrade to 10.04.1, I see the 173 driver is disabled and a newer driver for the card is now in use.

I could try removing the new driver and re-enabling the old. The biggest worry about going this route is that Lucid suffers from video chip and card-related freezes:

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

A friend of mine was bitten by this when he upgraded (his solution was to buy a video card to bypass his Intel chip). 

So if I did go this route, I run into the danger that I might lock up the whole system and would need to re-install the new driver. Any idea on how to do this in recovery mode if it came to that?

StewartM

---

### Post by no2498 on 2010-08-12
the cam driver for most all cams are in the kernel now days
the card may be a part of the problem not not all of it

this comes from cheese webcam booth 

You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
 


try that instead

---

### Post by StewartM on 2010-08-13
Turns out that when I restarted my computer, it fixed not only tha problem, but the Firefox problem of not being able to use encrypted space for user profiles. 

I also did re-enable the old NVIDIA video driver and that allows the webcam to work with the 2.6.32-22 kernel, with Ekiga, Skype, Cheese, and Flash. I'll mark this thread as solved.

StewartM

---

