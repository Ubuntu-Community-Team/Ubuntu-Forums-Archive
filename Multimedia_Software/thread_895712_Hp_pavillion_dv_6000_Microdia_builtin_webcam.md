---
title: "Hp pavillion dv 6000 Microdia builtin webcam"
date: 2008-08-20
forum: Multimedia Software
---

### Post by livevil on 2008-08-20
Hi! I have some problems to install my built in webcam, in the specific by loading the uvcvideo module. I'm reading this wiki:
[http://wiki.ubuntu-it.org/Hardware/Webcam/HpPavilion?highlight=(webcam](http://wiki.ubuntu-it.org/Hardware/Webcam/HpPavilion?highlight=(webcam))

This is the error:

maurizio@maurizio-laptop:~$ sudo modprobe uvcvideo
[sudo] password for maurizio:
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-19-generic/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)


lsusb and dmesg results are attached 

The webcam before worked correctly, after tryng to install the pciexpress tvtuner drivers something wrong happened!!!:(

Now with cheese is displayed the attached image.

I hope someone can help me.
Thank's

---

### Post by Crafty Kisses on 2008-08-25
You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2).

---

### Post by ramirabeau on 2009-02-13
:confused:I am having a similar problem with my webcam. It works fine with no tweaks through Ekiga, but with Kopete KDE 4.1.2. it gives the following error:

I cannot find the Jasper image conversion program.
Jasper is required to render the Yahoo webcam images.
Please see [http://wiki.kde.org/tikiindex.php?page=Kopete%20Webcam%20Support](http://wiki.kde.org/tikiindex.php?page=Kopete%20Webcam%20Support) for further information.

When I go to settings>configure in Kopete the cam comes on and all seems good. I must be missing something simple because it will not allow me to use the cam in a chat. The cam is v4l2 capable. All other features of the laptop work fine. Any help would be appreciated. 

HP DV6446us/2GHz Intel Dual Core/2GB/160GB/Ubuntu 8.04

---

