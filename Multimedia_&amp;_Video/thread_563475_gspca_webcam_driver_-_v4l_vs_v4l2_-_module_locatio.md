---
title: "gspca webcam driver - v4l vs v4l2 - module locations"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by skullmunky on 2007-09-30
i hava logitech quickcam chat, and i'm trying to use it with V4L2.  Actually I'd like to be able to use it with both V4L1 and V4L2, because I have some apps that want one and some that want the other. 

I built and installed  the gspca driver from mxhaard (=god!!).  plugged the  quickcam in and fired up camstream, and it worked fine.  but when i try running my own code or anything that expects V4L2 i get an error that there are no video4linux2 devices.  i figured out after a bit that gspca is by default only v4l1 and to get v4l2 you have to download the development branch.  got that to build and install, but no change.  here's where things get puzzling.

i tried uninstalling and reinstalling gspcav1 and gspcav2 drivers, just to see if there was any change.  no matter what, dmesg always gave the same results.  at one point i removed both; and the cam still worked - weird!    and here's why.  kernel modules go into

 /lib//lib/modules/2.6.20-15-generic/kernel/

building gspca from source puts it in usb/media

or in 

drivers/media/video

but, it turns out there is another copy already in 

ubuntu/media/gspcav1


whaddya know - i guess it comes with 7.04 by default and i didn't need to compile anything!  

except i still want V4L2 support.  So i tried nuking that one, but now can't get my compiled gspcav2 driver to do anything.  modprobe loads it without errors, but when i plug in the webcam it doesn't pick it up and attach /dev/video0.   and, i have to manually modprobe it, where it should be getting loaded automagically by udev or whatever, right?  

so, first question, i don't know the module tree well, is there something special about the ubuntu/ directory, and do i need to do anything else to somehow register a module properly?  does it matter which directory it's in?  

second, do i need to edit the udev rules to make this work properly?

third, if i have an app that is written for v4l2, how hard is it to convert it to v4l1 and vice versa?

---

