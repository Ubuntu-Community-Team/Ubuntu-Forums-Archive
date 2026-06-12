---
title: "Cheese can't detect webcam"
date: 2010-02-03
forum: Multimedia Software
---

### Post by ngronewold on 2010-02-03
I have a Dell Inspiron 1420 laptop with a built-in webcam.  I installed Cheese months ago and it worked fine then -- pics, videos, the works.

Now, after some updates recommended by Canonical, Cheese is telling me that it can't find the webcam.  I tried dumping it an reinstalling, but to no avail.

Anyone out there know what's going on?  Did the updates knock out a hardware driver?  Thanks.

---

### Post by garryknight on 2010-02-03
The same happened to me with my Advent 4211-B (MSI Wind clone) netbook after I let it upgrade Kubuntu 9.04 to 9.10. So I'm reverting to 9.04, which should solve a few other problems too (USB not always detected, HuaWei dongle intermittently doesn't work).

---

### Post by no2498 on 2010-02-05
you needed to look in cheese's help files faq

open a terminal type ( gstreamer-properties ) click enter
try v4l1 or v4l2 go try cheese

---

### Post by ngronewold on 2010-02-06
Ok, now it's working even though I didn't do a thing.  I guess I just have to think happy thoughts to make it work. Thanks guys.

---

### Post by garryknight on 2010-02-07
Now I wish I'd asked you to think about mine before I downgraded. :D

---

### Post by jmgold on 2010-11-13
I was having the same problem with cheese and ubuntu 10.10... used gstreamer-properties to switch from v4|2 to v4|1, which did the trick!

---

### Post by no2498 on 2010-11-15
glad to see it helped you

---

### Post by mo7ard on 2011-06-01
Hi,

When using Ubuntu 10.10 cheese runned just fine, but now that I'm running Ubuntu 11.04, it doesn't detects my webcam... can anyone help me?

THe webcam is detected and runs perfectly in Camorama and Kamoso, and when I run gstreamer-properties the video plugin is set to V4|2, but it doesn't has the option of V4|1... only "test input" and a custom setting option.

So the problem seems to be in Cheese. I reinstall it but it still shows pitch black... no webcam signal.

Thanks!!

---

### Post by no2498 on 2011-06-02
try this program wxcam
you can get it as a deb file 
just try 1 till it lodes 

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by mo7ard on 2011-06-02
> **no2498 said:**
> try this program wxcam
you can get it as a deb file 
just try 1 till it lodes 

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

Hi, thanks for the tip... wxcam seems to be simply brilliant!! :D And it's working just fine with my webcam.

But still... why is Cheese not working...? Don't get me wrong, for what I s've just seen, I'll be using wxcam for now on, but I'm just wondering why Cheese... :(

By the tests I made, wxcam is using video4linux2, just like Cheese (I think... correct me if I'm wrong), so... why... ooohh why... :p

Thanks a lot, no2498!! Great tip ;)

---

### Post by no2498 on 2011-06-03
im on 10.04 and had to reset gstreamer-properties like 10 times to keep mine working

did you change the place for cheese to put the pic/video's
that seems to kill it for mine

---

### Post by Wobblybob on 2011-06-03
I've given up on Cheese too I tried all the fixes here and still had no look but camorama works with no problems. using 64 bit xubuntu 11.04

---

### Post by mo7ard on 2011-06-07
> **no2498 said:**
> im on 10.04 and had to reset gstreamer-properties like 10 times to keep mine working

did you change the place for cheese to put the pic/video's
that seems to kill it for mine

Hi, that seems to be a good tip, but I'm now using wxcam... it's brilliant, although cheese layout is better.

Strangely enough, cheese runs well with my other USB webcam (a simple wired USB webcam) but with this new one (wireless webcam with USB 4 channel receiver) only works in Ubuntu 10.10. I've tried in my laptop and desktop computer, with the same result.

I'll be putting cheese apart, and use only wxcam... I just love this app.

Thank's to you all ;)

---

### Post by tastefuldeath on 2012-01-11
:( My netbook webcam can't be detected too, also by skype and stuff. I tried some things suggested by a friend. Weirdly, I was able to make it work before. 

> lkirsten@Kirsten-N150P:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 003 Device 002: ID 0a5c:219c Broadcom Corp. 
kirsten@Kirsten-N150P:~$ gstreamer-properties

(gstreamer-properties:2561): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:2561): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
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
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]

Any other ideas?

---

