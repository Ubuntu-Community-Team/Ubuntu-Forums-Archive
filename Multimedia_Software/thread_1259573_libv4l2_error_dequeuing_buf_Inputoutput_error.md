---
title: "libv4l2: error dequeuing buf: Input/output error"
date: 2009-09-06
forum: Multimedia Software
---

### Post by omax on 2009-09-06
I get the following error when I try to run my webcam (Creative NX Ultra) in any program.

libv4l2: error dequeuing buf: Input/output error

#lsusb
Bus 005 Device 002: ID 041e:401d Creative Technology, Ltd WebCam NX Ultra

$ lsmod | grep gspca
gspca_spca505          16384  0 
gspca_main             34432  1 gspca_spca505
compat_ioctl32         18304  1 gspca_main
videodev               45184  2 gspca_main,compat_ioctl32

I've tried everything. Nothing works. How do I fix this?

---

### Post by bifferos on 2009-11-15
> **omax said:**
> 
libv4l2: error dequeuing buf: Input/output error

I've tried everything. Nothing works. How do I fix this?

This isn't an Ubuntu-specific bug, I've been scratching my head over this for a while.

I've got a slow embedded device called a Bifferboard ([www.bifferos.com]("http://www.bifferos.com"), 150Mhz 486 CPU board) which exhibits the problem with my pac207 webcam every time.  I've tried with 2.6.30.1, 2.6.30.5 and 2.6.32-rc7 all give this error.

I've compiled the same kernels on my laptop, but it works fine there.  I even tried reducing my laptop memory to the 32MB like the Bifferboard, but still it works on the laptop, so I think it must be a speed/timing issue.  I would like to reduce the CPU speed on my laptop to further test out this theory, but I don't know how to drop a Pentium M below 600MHz.

My laptop uses UHCI, (not OHCI) but I can't believe that's making the difference.

regards,
Biff.

---

### Post by rarsa on 2010-08-14
Have you tried disconnecting all other USB devices from your computer and leaving just the Webcam?

I am still trying to figure out why other devices may be conflicting with the camera.

[http://kwlug.org/node/759](http://kwlug.org/node/759)

I am using the following camera under Lucid Linx

Bus 002 Device 003: ID 046d:0870 Logitech, Inc. QuickCam Express

Please let me know if unplugging the other USB devices works for you.

---

### Post by no2498 on 2010-08-14
5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.
    
5.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in "gstreamer-properties". If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.
    
5.5.&#8195;Where does Cheese store my photos?


      Your photos are stored in ~/.gnome2/cheese/media. You can also save
      them to an alternate location from within Cheese. Please see the help
      topic titled "Saving photos and videos to an alternate location" for
      information on this.
    
5.6.&#8195;My Quickcam Express doesn't work with Cheese...


      or gstreamer, and I see errors like "Not enough buffers. We got 1, we
      want at least 2" in the Cheese output. With driver "qc-usb".
    


      Try running "qcset /dev/video0 compat=dblbuf" to enable double buffer
      compatibility mode, then restart Cheese
    
5.7.&#8195;Which cameras are supported


      Cheese uses gstreamer for video grabbing. So in principle Cheese supports 
      any camera that works with GStreamer. In principle that should be any camera
      which support video4linux or video4linux2.
    

look at 5.6



this comes from the cheese help file faq's

---

