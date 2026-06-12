---
title: "Upside Down Webcam"
date: 2010-10-14
forum: Multimedia Software
---

### Post by mncjr94 on 2010-10-14
I have an Asus K series laptop and i recently got ubuntu.  The built in webcam seems to show me upside down in any webcam software.  I have no idea how to fix this and i have the latest drivers.  Helppp

---

### Post by SteveDee on 2010-10-15
See this thread: [http://ubuntuforums.org/showthread.php?t=1580848](http://ubuntuforums.org/showthread.php?t=1580848)

---

### Post by lidex on 2010-10-17
> 5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.
*~jsevi83*

Reference:
[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

---

### Post by oregonbob on 2010-10-17
I have a ASUS K50ij running 10.04. I tried the above instructions, no errors doing iy but it didn't fix it. It is still upside down.

Then I searched and found a "flip_webcam" download and recipe. It didn't work because flip_webcam gave error:
bash: /bin/flip_webcam: cannot execute binary file

The last time I tried recipes from this forum for hours until it drove me nuts.

---

### Post by lidex on 2010-10-17
> **oregonbob said:**
> I have a ASUS K50ij running 10.04. I tried the above instructions, no errors doing iy but it didn't fix it. It is still upside down.

Then I searched and found a "flip_webcam" download and recipe. It didn't work because flip_webcam gave error:
bash: /bin/flip_webcam: cannot execute binary file

Did you install 'gtk-v4l'?

---

### Post by oregonbob on 2010-10-17
Yes, I installed gtk-v4l. It runs without error, but there is no adjustments for orientation, only brightness, contrast type adjustments.

---

### Post by lidex on 2010-10-17
> **oregonbob said:**
> Yes, I installed gtk-v4l. It runs without error, but there is no adjustments for orientation, only brightness, contrast type adjustments.

Gotcha. I didn't delve to deeply into that thread - wonder what was referred to exactly as the fix then.

---

### Post by mncjr94 on 2010-10-31
bahhh ive been trying to get this fixed forever and i still cant get it done

---

### Post by jd2012 on 2011-01-29
Sorry for the 3 month old bump.

Ran:
```

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

```
Installed, but can't seem to find a GUI ect. Not quite sure how to adjust camera settings as it said was able to do. :confused:

Did:
```

sudo gstreamer-properties

```

Went into "Video" and did a test, camera is right-side up.:P
VLC, upside down.:(
Question is how do I get it right side up on my browser using sites like chatroulette or omegle?

Thanx.

---

### Post by firefya on 2011-03-14
> 5) WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

There is a nice utility to adjust the settings of our webcam (whitebalance, light, ...) called gtk-v4l.

Tried this, worked fine. Installed gtk-v41 (after entering the command line)via synaptics, camera and video functioning correctly.

---

### Post by phthoruth on 2011-03-14
Can anyone confirm that this issue still affects Google Talk Video?

---

### Post by the_paco on 2011-04-01
It's still there. Running adobe flash on FF4 on 10.04x64 on an Asus G50v. gtk-v4l doesn't touch it. Other apps run fine, just flash seems to have this problem for me. Cheese and standalone cam apps work fine.

---

### Post by the_paco on 2011-04-30
Per [http://www.ideasonboard.org/uvc/:](http://www.ideasonboard.org/uvc/:)   IF your webcam is UVC
[INDENT]Check for UVC by running in terminal:          
[INDENT]lsusb      
[/INDENT]and finding your webcam in the resultant list.      It should say it next to it in a perfect world. If it doesn't look through the beginnings of this old thread:
[http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210) and you may find out more.

[/INDENT]AND you're running the Video 4 Linux 2 plugin...      
[INDENT]You can see by running in terminal: 
[INDENT]         gstreamer-properties      
click on 'video' at the top of the resulting window, check the plugin.  
[/INDENT][/INDENT]Then you can check to see if your webcam is giving them fits on the V4L2 plugin website: [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)  
You can check their list of known devices and find yours based on the device ID and see if there are any known issues or if they even know about your device. You may be able to find a fix there. 

The answer they gave me about mine though was: 
[INDENT] **"This camera module is known to be mounted upside-down in some notebooks. Applications that use the libv4l library should display the video correctly, as libv4l detects upside-down cameras and rotates the image automatically. See Hans de Goede's post on the linux-uvc-devel mailing list for more information. For applications that don't use libv4l, try holding your computer upside-down."** 
[/INDENT]So for google chat and other plugins for Firefox I'm kind of hosed. I'm off to find what Firefox and/or google use to access my webcam.

Edit: Google-fu is strong yet ability to make post is weak!
searching for "get firefox to use v4l2" yielded this page from 2008:
[http://www.jtolds.com/newsletter/2008/7/27/how-to-get-v4l2-devices-to-work-with-flash](http://www.jtolds.com/newsletter/2008/7/27/how-to-get-v4l2-devices-to-work-with-flash)
and from 2008 as well:
[http://blogs.adobe.com/penguinswf/2008/07/paparazzi_v2_1.html](http://blogs.adobe.com/penguinswf/2008/07/paparazzi_v2_1.html)

But they say Flash 10 beta 2 should have support for V4L2 devices like mine! I'm 10.2.159.1 per the website and Synaptic, so what gives? Update to follow, testing something.....

---

### Post by the_paco on 2011-04-30
You know, I could have sworn I'd done this before.... but.
[http://techspalace.blogspot.com/2010/11/upside-down-cam-fix-for-flash-and-other.html](http://techspalace.blogspot.com/2010/11/upside-down-cam-fix-for-flash-and-other.html)
This post details out how to load and run the V4Lv1 compatibility fix for the applications. IE: I load and run:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so firefox

and boom. Firefox with my webcam corrected. Maybe I was loading from a different repo, but the instructions are referenced at the top of that post. I'm still searching for some hint that Flash will begin implementing V4L2.... I don't understand it all, really. I don't know anything about flash or how it accesses my hardware, just that they seem to think they need to reinvent the wheel rather than use the drivers I've already loaded.

I'll look into the open-flash alternatives and see if they did it any different.

---

