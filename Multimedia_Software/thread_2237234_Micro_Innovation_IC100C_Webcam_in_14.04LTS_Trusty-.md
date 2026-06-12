---
title: "Micro Innovation IC100C Webcam in 14.04LTS Trusty-Tahr"
date: 2014-07-31
forum: Multimedia Software
---

### Post by george-pentagon on 2014-07-31
Hi,
i am running the latest Ubuntu 14.04 LTS.
i have a very old MicroInnovations IC100C Webcam.
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations)


i was trying to make it work in Ubuntu with Cheese/Skype/guvcviewer/wxCam .....
same problem as this one thread....
[http://ubuntuforums.org/showthread.php?t=1239835](http://ubuntuforums.org/showthread.php?t=1239835)




I google a lot.... found this...


I tried hard to do what the following tutorial video instructs... 
"Get Your Webcam working with GSPCA Tutorial...."

[FONT=arial]http://www.linuxjournal.com/video/get-your-webcam-working-[/FONT]**gspca**




but I can't figure out how to make changes for the latest ubuntu kernel setup... so the build/make gspca_build file is not compiling properly and is giving many errors like :
 <linux/config.h> not found,
<asm/semaphore.h> not found,
<linux/videodev.h>.... etc....

I tried commenting out those include statements in the gspca.h, gspca_build.c files, like in some forum-posts i read,
and it still didn't complete compiling, with eve more warnings and other errors....


I would be really grateful if the camera could somehow start working...


right now, when i check gstreamer-properties, only 'v4l2src' option is there and doesn't produce a video on test.......


my intuition and reading many forum posts tells me, 'v4l1src' option needs to be available....
My problem seems very similar to this forum-post :
"Missing gstreamer plug-in 'v4lsrc' in Ubuntu 12.04"
[http://ubuntuforums.org/archive/index.php/t-2032082.html](http://ubuntuforums.org/archive/index.php/t-2032082.html)


Cheese software and skype gives a black screen... 
both detect a device 'icam320' using 'spca508' driver.


Cheese software says there is a 'frame-format' error and to select correct format-setting in 'preferences menu'.


I am willing to give more information to get this solved... Please Help.
---------------------------------------------------------------------------------------------------------

I found this, looks like an answer :
[http://www.armadeus.com/wiki/index.php?title=GspcaWebcam](http://www.armadeus.com/wiki/index.php?title=GspcaWebcam)

in a terminal, i tried : "make linux-menuconfig"
I got the error: 
"make: *** No rule to make target `linux-menuconfig'. Stop."

---

### Post by george-pentagon on 2014-08-01
when i run gstreamer-properties, i get the following warnings/errors before the gui opens up....
--------------------------------------------------------------------------------
root@desktop:~# gstreamer-properties


(gstreamer-properties:26920): Gtk-WARNING **: Unknown property: GtkDialog.has-separator


(gstreamer-properties:26920): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
root@desktop:~#
------------------------------------------------------------------------------------


Note: the 'v4lsrc' plugin is unavailabe message......


in video tab, default Input section , i only get: 
Plugin : Video For Linux-2 (v4l2),
Device: iCam320,
Pipeline:  v4l2src device="/dev/video0",


This webcam device, i believe requires the unavailable 'v4lsrc' plugin, so i can select 'v4lsrc' device = "/dev/video0",


How can I get this unavailable 'v4lsrc' plugin to load in gstreamer-properties ???


same as mentioned in this post:
[http://ubuntuforums.org/showthread.php?t=2032082](http://ubuntuforums.org/showthread.php?t=2032082)

---

### Post by george-pentagon on 2014-08-01
I googled "install gstreamer plugin v4lsrc",


all the forum-posts say 'v4lsrc' plugin was removed from repoistory around 2011....


is there any way to manually install 'v4lsrc' plugin and make 'v4lsrc' dependant devices work in ubuntu or any other linux os ?


something like this debian patch to include 'v4lsrc' plugin option ?
[http://lists.alioth.debian.org/pipermail/pkg-multimedia-commits/2013-April/033054.html](http://lists.alioth.debian.org/pipermail/pkg-multimedia-commits/2013-April/033054.html)


I also found this tool v4l-conf for drivers: 
v4l-conf  [ options ] 


options:
    -q        quiet
    -d <dpy>  X11 Display     [:0]
    -c <dev>  video device    [/dev/video0]
    -b <n>    displays color depth is <n> bpp
    -s <n>    shift display by <n> bytes
    -f        query frame buffer device for info
    -a <addr> set framebuffer address to <addr>
              (in hex, root only, successful autodetect
               will overwrite this address)
    -p <pitch> set framebuffer pitch to <pitch> bytes
              (decimal, root only)
    -1        force v4l API
    -2        force v4l2 API




is it possible to use option "-1 force v4l API" for v4lsrc webcams ?

---

