---
title: "Totem Video Player error"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Jammanuser on 2010-08-12
Hello.

I am having a problem with the Totem Video Player.
Sometimes when I try to play a perfectly good video in it, it displays an error saying the following:

> 
An error occurred

Could not get/set settings from/on resource


Usually, restarting and re-opening the video in Totem will remove the error, and allow me to play the video as normal. However, that's not working this time. And its a real pain.

Anyone have any idea how I can fix this?

Thanks in advance.

-Jam Man

:guitar:

---

### Post by no2498 on 2010-08-12
just a guess but try this it comes from cheese webcam booth


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you

---

### Post by Jammanuser on 2010-08-13
> **no2498 said:**
> just a guess but try this it comes from cheese webcam booth


You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you

Hmm...interesting. Mine was set to "Autodetect". So I'm not sure which one its using. But I changed it to "X Window System (X11/XShm/XV)", and we'll see how it goes.

I'll make sure to report what happens next. Thanks.

Cheers.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-08-13
Ok, I just pressed the "Test" button after making the above change, and it gave the following error:

> 
X Window System (X11/XShm/XV): Could not initialize Xv output


EDIT: Now, when I try to play a video in Totem, it displays this error instead:

> 
An error occured

The video output is in use by another application.
Please close other video applications, or select 
another video output in the Multimedia Systems
Selector.


And that's without any other video application running.

---

### Post by no2498 on 2010-08-14
reset it the same way

this is the cheese help file



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

