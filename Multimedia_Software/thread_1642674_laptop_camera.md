---
title: "laptop camera"
date: 2010-12-10
forum: Multimedia Software
---

### Post by siddi on 2010-12-10
My built in laptop camera stopped working when i changed from windows to ubuntu 8.10

now i have upgraded to ubuntu 10.10, and still the camera doesn't work.. 

can anyone please help?

---

### Post by gaelicbright on 2010-12-10
[LEFT][COLOR=#000000]More computers to the built-in webcam. They are designed to work with instant messaging and VOIP projects, such as Yahoo Messenger and Skype. Many photo editing programs, such as Google's Picasa, you can directly from their photographs. This article describes how to make your camera, with each of these free programs.
[URL="http://www.ehow.com/how_4882696_use-builtin-webcam-laptop-computer.html#ixzz17m9D7Izl"]
[/URL][/COLOR][/LEFT]

---

### Post by no2498 on 2010-12-11
try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

---

### Post by siddi on 2010-12-11
> **no2498 said:**
> try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1



This is not working for both options:(

---

### Post by azertyh on 2010-12-12
hello,
is the uvcvideo module loaded. for me,
```
lsmod | grep uvcvideo
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev

```

---

### Post by siddi on 2010-12-12
[[IMG]http://ubuntuforums.org/images/misc/ubuntulogo.png[/IMG]]("http://ubuntuforums.org/index.php")> **azertyh said:**
> hello,
is the uvcvideo module loaded. for me,
```
lsmod | grep uvcvideo
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev

```


hi
do i have to type this on the terminal one by one or together?

---

### Post by no2498 on 2010-12-13
do you need to push any key's to turn the cam on first

and look in sound and video for cheese webcam booth
try the cam in cheese

if not installed open a terminal type
sudo apt-get install cheese
pass word for sudo you will not see any thing just click enter

---

### Post by siddi on 2010-12-13
> **no2498 said:**
> do you need to push any key's to turn the cam on first

and look in sound and video for cheese webcam booth
try the cam in cheese

if not installed open a terminal type
sudo apt-get install cheese
pass word for sudo you will not see any thing just click enter


i don't need to push any keys.

---

### Post by no2498 on 2010-12-13
this is the cheese help faq's

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

### Post by azertyh on 2010-12-13
> **siddi said:**
> [[IMG]http://ubuntuforums.org/images/misc/ubuntulogo.png[/IMG]]("http://ubuntuforums.org/index.php")


hi
do i have to type this on the terminal one by one or together?

just the first line. the other lines are the result of the first line in my computer.

---

### Post by siddi on 2011-01-20
Still not working..... someone help...

---

### Post by no2498 on 2011-01-21
type webcam in a terminal click enter
that should install a cam grabber
i hope it helps

---

### Post by no2498 on 2011-01-21
find and install xawtv instead of webcam
it loads a grabber too

---

