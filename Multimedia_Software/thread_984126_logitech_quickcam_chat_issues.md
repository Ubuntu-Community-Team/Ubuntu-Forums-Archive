---
title: "logitech quickcam chat issues"
date: 2008-11-16
forum: Multimedia Software
---

### Post by saladbar2000 on 2008-11-16
Hello everybody.  It looks like I still have some webcam issues although I think I've made some progress thanks to linux23dragon.  My computer wasn't seeing my webcam at all after the upgrade but we were able to install the correct drivers for the logitech quickcam chat.  It looks like it isn't UVC compliant so we installed the gspa drivers.  

It now works but not correctly.  Cheese and ekiga now see the camera but everything is very dark and ekiga won't let me adjust the brightness and I'm not seeing anywhere to adjust the brightness for anything else.  I had to change everything to v4l2 setting for the camera to work but skype still doesn't see the camera and I'm not seeing how to make it see it.  

Any help would be greatly appreciated.

Dan

---

### Post by saladbar2000 on 2008-11-16
I found how to make the camera work in skype when I looked at this thread [http://forum.skype.com/index.php?showtopic=236711](http://forum.skype.com/index.php?showtopic=236711) which had a link to this thread [http://ubuntuforums.org/showthread.php?t=9...ght=skype+video](http://ubuntuforums.org/showthread.php?t=9...ght=skype+video).

I copied and pasted the command "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" and replaced "/v4l1compat.so" with "v4l2convert.so" and the camera worked when I tested it but it was really dark just like everything else. I guess now I've got to figure out how to adjust brightness.

---

### Post by Trafferth on 2008-11-18
Hello saladbar2000!

I am having similar issues.  I just had a good run at trying to get a Logitech QuickCam Chat to work, with partial success.

The following steps have netted me a picture (of sorts) in Ekiga and Cheese, but the camera is still not working correctly under Hardy (although it works just fine under WinXP SP3, as you'd expect with the original drivers).  Perhaps following this route might at least get you a basic picture to work with at some point along the route.

Firstly I tried installing drivers via EasyCam; the steps to which are documented under:

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

This detected my camera as a "Logitech QC  Elch2" and installed some drivers and cheese.  The output from cheese is overexposed and a strange green colour, but at least it was a picture of sorts.  For reference, my lsmod | grep gspca output is:
```

gspca                 643920  0 
videodev               29440  1 gspca
usbcore               146412  5 gspca,usbhid,ehci_hcd,uhci_hcd
```

While the lsusb output is:
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:092e Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 004: ID 06a3:8020 Saitek PLC 
Bus 001 Device 001: ID 0000:0000  
```

The 046d ID is a device type in principle supported (maybe only partially) by the open-source drivers installed by this procedure.

At this point, I am able to get an acceptable image in Ekiga using the built-in brightness and contrast controls.  It is low-resolution (much less than the 640x480 the camera is capable of), but at least it works.

Brightness controls in utilities like camorama, however, have no effect on the image (only Ekiga effects it so far), while cheese has no controls that I can see.  The image in Camorama is an odd shade of blue, and overexposed as before.

I downloaded and compiled v4l2ucp (v1.2), to see if I could manually change the exposure and saturation defaults, but my camera was not a supported device.  Incidentally, I had to edit the file 'v4l2ucp.cpp' and change the line (line 69 in the file I have) that reads 

```
w = MainWindow::openFile("/dev/video")
```

to

```
w = MainWindow::openFile("/dev/video0")
```

In order to correctly point to the webcam, but on compiling* and executing the program 'v4l2ucp' I am told that my webcam is not a V4L2 (Video For Linux 2) device.

* Note that you will need the qt development libraries to correctly compile this program.

At this point I have decided to research and purchase a new, fully Linux-compatible webcam for my Ubuntu box (my office machine), and use the current camera on my WinXP SP3 installation on my laptop.

I don't know if the above will be of use to you, but it gives you a starting point to try, at least.

You may also want to see if you can figure out a way of editing what I think are the webcam default parameters under

/sys/module/gspca/parameters/

I've not been able to figure out how you do this - gedit, nano, etc cannot open these files, even with root privileges, even though they are purportedly plain text files.  Strange...

Good luck!

Trafferth :)

---

### Post by GoLinux on 2008-11-29
Hi guys,

just got a Logitech QuickCam Chat myself (Walmart for $18.88 )). Just like you I get the very dark image, although the frame rate seems to be good, the motion is smooth.

At any rate, searching the forum and Googling around, I found a fix, although not optimal.

If you go here:

[http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/v4l2ucp.php](http://www.debian-multimedia.org/dists/stable/main/binary-i386/package/v4l2ucp.php)

You can download this application, v4l2ucp, which will allow you to control White Balance, Exposure and Gain of the QuickCam Chat (or any other webcam, I guess)

Once you adjust the parameters, they "stick" after you close it and Chesse, Ekiga and Skype show a decent image.

It is a Terminal application, but it has a graphical front-end. I created a launch icon on the desktop using "Create Launcher..." (right click on the desktop).

Here are some additional information on the program:

[http://www.spinics.net/lists/vfl/msg39018.html](http://www.spinics.net/lists/vfl/msg39018.html)

[http://sourceforge.net/projects/v4l2ucp/](http://sourceforge.net/projects/v4l2ucp/)

By the way, I'm using Ubuntu 8.10 out of a USB Flash Drive (no HDD installation). My computer is a Thinkpad T41. My skype version is the Skype-static (version 2.0.0.72). I had to use this to resolve the green screen issue and the crashing....

Try v4l2ucp and good luck!!!!

---

