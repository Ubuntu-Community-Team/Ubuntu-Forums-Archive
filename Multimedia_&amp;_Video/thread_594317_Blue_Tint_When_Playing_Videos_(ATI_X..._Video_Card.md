---
title: "Blue Tint When Playing Videos (ATI X... Video Card)"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by broth420 on 2007-10-27
I have had the same problem with both 7.4 and 7.10.  On 7.4, I follow the instructions to install the ATI video card (the sticky that now seems to be gone that was in the beginners section), reboot, and then enable the restricted driver.  Everything works great, but all of my video has a blue tint.
Tonight I did a clean install of 7.10, and the driver install is a little easier, but I end up with the same results.  I can disable the restricted driver, and the video looks normal, but my resolution isn't correct (I am using a widescreen monitor running at 1680x1050).
While I don't really use this system for video very often, I am kind of psychotic about having an error free system.  Any help would be appreciated.  I am sure there are all kinds of things I am missing, I am pretty new to Ubuntu.

---

### Post by tuntunazo on 2007-10-30
i have the same problem with an intel video card, in 7.4 and 7.10, when i play videos an move the window. i have a friend with the same prob

---

### Post by feiyang on 2007-10-31
You can try this :

( From this thread :
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373) )

aunch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Test .....

---

### Post by broth420 on 2007-11-03
That did the trick.  Thanks for your help.

---

### Post by 5h4rk on 2007-11-11
> **feiyang said:**
> You can try this :

( From this thread :
[https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373) )

aunch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

Test .....

What am I suppose to see when I clck test?

I did that but I still getting the blue background when I try to drag the video window.

---

### Post by einherier on 2008-01-28
I had trouble understanding what to do at the command prompt as I was having the same problem

1. I opened the command prompt
2. I finally figured out to type "gstreamer-properties"

then I changed the pipeline to custom and it fixed my problem straight off

thanks everyone

---

### Post by einherier on 2008-01-28
> **5h4rk said:**
> What am I suppose to see when I clck test?

This is what i got:
[[IMG]http://img295.imageshack.us/img295/6136/88342376jn8.th.png[/IMG]](http://img295.imageshack.us/my.php?image=88342376jn8.png)

---

### Post by fulmitz on 2008-02-19
Thanks,  this fixed my video playback however when I use my webcam in Skype 2.0 and run the test it has a blue hue.  When I turn off the device specific drivers color saturation is normal.  When I run gstreamer-properties and test the cam on the bottom half the color is normal as well.  Any suggestions would be appreciated. 

Thanks,

Fulmitz

---

### Post by go_beep_yourself on 2008-05-11
This couldn't possibly fix my problem because I am using xine. I have totem-xine. Any ideas?

---

