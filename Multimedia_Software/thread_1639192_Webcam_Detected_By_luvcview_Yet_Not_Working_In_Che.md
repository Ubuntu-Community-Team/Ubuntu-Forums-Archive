---
title: "Webcam Detected By luvcview Yet Not Working In Cheese"
date: 2010-12-06
forum: Multimedia Software
---

### Post by rykel on 2010-12-06
Hi, I bought a EG ACCESSORIES 5-megapixel webcam.

It did NOT come with any Windows driver, so I assumed that it is true 5mp AND will work out of the box with Ubuntu Maverick.

The strange thing is, it does work with luvcview, but NOT with Cheese. The latter 2 software cannot seem to detect the webcam.

Please help?

**UPDATE 7 Dec 2010** - When the webcam is unplugged and I do a ls /dev/video* I get the error message, "***ls: cannot access /dev/video*: No such file or directory***". When I plugged it in, it says, "***/dev/video0***". When I use VLC Player to play, my webcam WORKS. But still NOT Cheese. So where does the problem lie?

$ **lsusb**
[B]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 029: ID 1e4e:0100  
Bus 001 Device 027: ID 04f9:0033 Brother Industries, Ltd 
Bus 001 Device 025: ID 04d9:2519 Holtek Semiconductor, Inc. 
Bus 001 Device 024: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/B]

---

### Post by no2498 on 2010-12-06
cheese uses gstreamer you need to have the
gstreamer good, bad,ugly,and 10 installed
look in your package manager look for gstreamer

btw cheese has a nice help file look at the faq's

---

### Post by rykel on 2010-12-06
Hi, as you can see from the screenshot, I already have all the latest Maverick gstreamer good+bad+ugly+10 installed. What else could be (mis)configured?

---

### Post by no2498 on 2010-12-07
type  webcam   in a terminal click enter it should load a webcam grabber

hope it helps

---

### Post by rykel on 2010-12-11
bump

Hi, is there nobody who can help me with this problem in Ubuntu? coz I really would like to use the webcam... since it is workable in luvcview and vlc yet not in cheese, it is very troublesome to me!

btw, for the "run webcam in terminal" suggestion, thank you but it does not load any video... this is what I get:

[B]$ webcam
reading config file: /home/aen/.webcamrc
ioctl: VIDIOC_QUERYCTRL(id=9963803;type=unknown;name="";minimum=0;maximum=0;step=0;default_value=0;flags=0): Input/output error
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

[/B]

---

### Post by no2498 on 2010-12-11
from what i seen all the gstreamer's is not installed

---

### Post by no2498 on 2010-12-11
sorry i did not read it right

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

if cheese still does not work

if you use 32 bit try wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

and for sound

[http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/](http://u8untu.blogetery.com/2010/08/26/getting-wxcam-working-with-lucid/)

---

### Post by rykel on 2010-12-12
Hi, when I tried gstreamer-properties and tested both v4l and v4l2, the results are as follows:

[B][LIST=1]
[*]Video for Linux (v4l): Could not get/set settings from/on resource.

[*]Video for Linux 2 (v4l2): Failed getting controls attributes on device '/dev/video0'.
[/LIST][LIST=1]
[/LIST][/B]

I did not try wxcam as it does not come as a deb. However, it is strange if a webcam does not work with Cheese...

---

### Post by no2498 on 2010-12-13
you can get wxcam in a deb file or look in the package manager
5 mp may be too much for cheese

cheese has a bug tracker look in the faq's

5.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in "gstreamer-properties". If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.

---

### Post by rykel on 2010-12-30
I just discovered another weird issue with this webcam.

When connected to a Windows XP machine and then doing a Skype video call with my present Ubuntu Maverick machine, the Windows guy can see me on his screen, but I cannot see him on my screen. (blank)

However, when I Skype with him using a different Ubuntu Maverick machine, everything works perfectly.

Windows to Windows Skype there is NO problem. (again, this webcam did NOT need any Windows driver - no driver CD needed!)

Based on the above information, I suspect that there is no problem with the webcam itself or Ubuntu Maverick. Just that my present Ubuntu Maverick machine (which was upgraded from release to release) might have some missing/corrupted video rendering files.

Can you help me please?

---

