---
title: "Getting web cam to work with Skype"
date: 2009-06-18
forum: Multimedia Software
---

### Post by pokeyThePenguin on 2009-06-18
lsusb:
Bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 

lsmod | grep videodev:
videodev               29440  1 uvcvideo

I installed Cheese, and my web cam works with that.

I installed luvcview. When I ran it, I got this message:
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 22.
Init v4L2 failed !! exit fatal 


I'm using:
Ubuntu 8.04
Skype 2.0.0.72


Under Video Devices in the Options window, it says "CNF7051 (/dev/video0)", and that's the only option. When I click 'Test', Skype quits.

When the person I'm talking to lets me view their web cam, it's not clear at all. It's fuzzy and colourful.

When I try letting someone view my cam, Skype quits.

Any ideas what's wrong and how to solve the problem?

---

### Post by Tamara Perera on 2009-06-18
I don't see any other problems with your webcam in this command. But I think there are dependencies problem with skype. You can reinstall this software then try again. cause everytime I install skype it automatically detects my webcam. But the first time i have heard about such kind of case with skype.

---

### Post by gyarus on 2009-06-18
I found this thread of interest because I am about to buy a webcam to use with Skype.

Given the difficulty I had getting my microphone to work, what webcam would you recommend?

---

### Post by pokeyThePenguin on 2009-06-19
I did:
sudo apt-get remove --purge skype
sudo apt-get install skype

I still have the same problems, though.

---

### Post by pokeyThePenguin on 2009-06-19
I ran skype in the terminal to see its output when I run the video test:

skype
Starting the process...
Skype Xv: Xv ports available: 0
Skype XShm: XShm support enabled
Aborted


I also tried:
export LIBXCB_ALLOW_SLOPPY_LOCK=1

But that didn't change Skype's behaviour (still crashes).

---

### Post by pokeyThePenguin on 2009-06-19
Installing skype-static had no effect either.

---

### Post by sridatta on 2009-06-19
Your question is most likely resolved in this thread: [http://ubuntuforums.org/showthread.php?t=993262](http://ubuntuforums.org/showthread.php?t=993262)

Just paste this into terminal
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by Simpotico on 2009-06-19
I'm having the same problem... My Pixxo webcam works just great with Ekiga but when I turn on Skype and test it, I just get a rainbow snow show.

---

### Post by pokeyThePenguin on 2009-06-19
I grabbed libv4l from here: [http://freshmeat.net/projects/libv4l](http://freshmeat.net/projects/libv4l)

make
sudo make install
LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so skype

No effect.

I'm wondering why no Xv ports are available.

---

### Post by pokeyThePenguin on 2009-06-19
Anyone know how to install Xv on Hardy Heron?

When I run gstreamer-properties to change the default output to Xv, I get this:
gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'X Window System (X11/XShm/Xv)': Could not initialise Xv output [xvimagesink.c(1333): gst_xvimagesink_get_xv_support (): /pipeline0/xvimagesink2:
No port available]

---

### Post by pokeyThePenguin on 2009-06-19
I'm not having any luck finding an up-to-date tutorial on how to install Xv on Hardy Heron.

Any help would be greatly appreciated.

---

### Post by pokeyThePenguin on 2009-06-20
SOLVED! :)

Solution: install proprietary driver for ATI card: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by Simpotico on 2009-06-22
The code worked for me... Bit of a pain but I'll study up on the other two links suggested in this thread and get back with which one worked for me.

Intrepid 8.10

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

