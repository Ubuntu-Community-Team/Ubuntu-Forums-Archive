---
title: "Video recording in cheese freezes on ASRock ION 330 after upgrade to Lucid"
date: 2010-08-12
forum: Multimedia Software
---

### Post by lakshman_ab on 2010-08-12
H/W: *ASRock ION 330*
*Ubuntu 10.04 LTS - the Lucid Lynx and Windows 7 64 bit on dual boot*
*logitec QuickCam Pro 9000*
**uname -a**
*Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux*

I recently upgraded from karmic koala to lucid and it looks like that cheese is using the CPU rather than ION when recording which means it  simply freezes with near 100% CPU usage.
Any ideas folks?

In System->Administration->Hardware drivers the recommended NVIDIA driver is currently active and in use.

$ **sudo apt-get install nvidia-current***                         
[sudo] password for lab1301: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-current for regex 'nvidia-current*'
Note, selecting nvidia-current-dev for regex 'nvidia-current*'
Note, selecting nvidia-current-modaliases for regex 'nvidia-current*'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by no2498 on 2010-08-12
this comes from the cheese help faq's


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    





try that see if it helps

---

### Post by lakshman_ab on 2010-08-12
> **no2498 said:**
> this comes from the cheese help faq's


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
try that see if it helps


Thanks for the prompt response.
As suggested I've set the *Default Output Plugin* field in "Multimedia System Selector" (as displayed by utility *gstreamer-properties*) to X Window System (X11/XShm/Xv).  But, no joy I'm afraid.  However, when I test the default input I can see the web cam picture but not when I test the default output.
I've also done a cut and paste of the o/p from cheese -v  when recording below.
I'm investigating further...

The output from *gstreamer-properties* is as follows:
**gstreamer-properties**
[I](process:2660): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
[/I]

Cut and paste of output from cheese when recording:
$ **cheese -v**

(process:2859): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Cheese 2.30.1 
** Message: Error: Stream contains no data.
gsttypefindelement.c(939): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

totem-video-thumbnailer couldn't open file 'file:///home/lab1301/Videos/Webcam/2010-08-12-224838.ogv'
Reason: Stream contains no data..

** (cheese:2859): WARNING **: could not generate thumbnail for /home/lab1301/Videos/Webcam/2010-08-12-224838.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/lab1301/Videos/Webcam/2010-08-12-224505.ogv'
Reason: Took too much time to process.
totem-video-thumbnailer couldn't process file: 'file:///home/lab1301/Videos/Webcam/2010-08-12-005440.ogv'
Reason: Took too much time to process.

** (cheese:2859): WARNING **: could not generate thumbnail for /home/lab1301/Videos/Webcam/2010-08-12-224505.ogv (video/ogg)


** (cheese:2859): WARNING **: could not generate thumbnail for /home/lab1301/Videos/Webcam/2010-08-12-005440.ogv (video/ogg)

---

### Post by no2498 on 2010-08-13
i can not get my webcam to come on in totem myself

i do like this program wxcam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope that helps some

---

### Post by lakshman_ab on 2010-08-13
> **no2498 said:**
> i can not get my webcam to come on in totem myself

i do like this program wxcam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope that helps some

My web cam works and I can take photos etc.  It's only when recording that I have an issue as the CPU is being hogged rather than the ION chip.   I have windows 7 on dual boot and don't have this issue there and I don't think I had this issue under Karmic koala either.

---

### Post by no2498 on 2010-08-14
all of the cheese help file



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

---

### Post by lakshman_ab on 2010-08-15
> **no2498 said:**
> all of the cheese help file



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

Thanks for the response and here is mine:

5.1 - Have already tried (see my post above)
5.2 - I have a ASRock ION and not a MAC.  See title of my thread
5.3 - Irrelevant as only recording is an issue (see title of my 
post)
5.4 - ditto
5.5 - ditto
5.6 - ditto
5.7 - ditto

---

