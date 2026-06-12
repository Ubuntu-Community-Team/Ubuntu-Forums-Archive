---
title: "Problem with Cheese Webcam Booth 2.32.0 on Ubuntu 10.10"
date: 2010-11-03
forum: Multimedia Software
---

### Post by neotheone2401 on 2010-11-03
Hey guys,

I am new to Linux Ubuntu, managed to learn a few trick of the trade, but I can't seem to get this thing straight. I used the Ubuntu Software Center to install the Cheese 2.32.0 on Ubuntu 10.10. I am using Ubuntu on Compaq CQ 60. Cheese worked for a few days and now it wouldn't show any image on the screen. Every time I run Cheese it sort of gives me a scrambled display:confused:  I have attached a screenshot for convenience.
Thanks in advance!!

---

### Post by marin123 on 2010-11-03
i think youre using effects... cheese remembers effects when you shut it down... see if any are highlighted.

---

### Post by neotheone2401 on 2010-11-04
@marin:

Hey marin, I tried disabling the **[COLOR=Red]effect[/COLOR]** by choosing Edit in the menu bar and unchecking the "effects" option, and restarted the application, but the problem is intermittent. :(
I have attached a screenshot in my original post!!

---

### Post by Hashiru on 2010-11-04
Hi, it might be a really stupid idea, but try uninstalling it and then install it again.
Maybe it works. 
To test if it isn't your webcam you might want to try booting a live cd or usb, install cheese and see if it works on the clean install. I've been trying to fix a broken webcam with software once, not a good idea ^^

---

### Post by marin123 on 2010-11-04
> **neotheone2401 said:**
> @marin:

Hey marin, I tried disabling the **[COLOR=Red]effect[/COLOR]** by choosing Edit in the menu bar and unchecking the "effects" option, and restarted the application, but the problem is intermittent. :(
I have attached a screenshot in my original post!!

unchecking the effects wont work... look carefully at each effect and see if its highlighted.. if it is, click on it to disable it.
its weird that it was running and now it isnt anymore.. if this doesnt work, try:

```
sudo apt-get install --reinstall cheese
```

to reinstall cheese...

---

### Post by neotheone2401 on 2010-11-06
@marin123:
Thank you!!! I will certainly try that

@hashiru:
I will certainly try that!!

---

### Post by neotheone2401 on 2010-11-06
Hey,
@marin and @hashiru,
I reinstalled cheese, but still no good, its the same :(
I have a Compaq CQ 60, HP Webcam!!

---

### Post by marin123 on 2010-11-06
try to run ubuntu from live cd and see what happens when you run cheese...

---

### Post by no2498 on 2010-11-07
cheese has a nice help file look in the faq's

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

### Post by neotheone2401 on 2010-11-22
Well I couldn't resolve the Cheese issue, it's intermittent, uninstalled Cheese and installed Camorama!!! He he he!!

---

### Post by fendijr on 2011-08-04
jimmy@jimmy-Aspire-4925:~$ sudo apt-get install --reinstall cheese
sudo: unable to resolve host jimmy-Aspire-4925
[sudo] password for jimmy: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jimmy@jimmy-Aspire-4925:~$ 


how to settle this?
is it set up on software sources not right?
anyone could help me?

---

### Post by marin123 on 2011-08-04
are you running software update or synaptic in the background?
thats what that message means. some other app is using sudo to install something.

---

