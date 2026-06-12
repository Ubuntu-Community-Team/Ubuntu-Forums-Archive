---
title: "Logitech Webcam Not Working"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by Noodels on 2007-09-30
I've tried looking on other threads but it seems that everyone is substantially further than me in getting their webcams working, i.e. it's been detected.

I have gotten nowhere, it is a usb logitech webcam, (CAV 2 is written under the base) but apart from that I know nothing about it. I do not know how to do anything with it, can I make it take a picture or a video? How? In windows it installed its own software, so this is difficult. (Damn you windows for making me webcam incompetent!)

---

### Post by skullmunky on 2007-09-30
Hi noodels,

hoping someone can help me solve -my- webcam troubles, here's what i can tell you for yours.

First: yes, you probably can.  you need a webcam driver and you need a program to capture images with.  for the driver, a lot of logitech cams work with the "GSPCA" driver, which I think maybe even comes with Ubuntu already.

There are a whole slew of programs for working with webcams.  Kopete, the chat program, will let you do video chat, for example.  

I like a program called "camstream" just for capturing images and for testing.  To get it, open up Synaptic, search for "camstream", and install it.  or, from the terminal:

sudo apt-get install camstream

you launch camstream from the terminal too, just by typing "camstream".

if it recognizes your webcam already, when you go to File->Open Viewer... It will give you a list of available devices (webcams).  If that menu's empty it means you have to install the driver.

INSTALLING THE DRIVER (GSPCA)

Maybe this is the right one for your webcam, maybe not.  But let's try it.

1. Open Synaptic
2. look for "GSPCA"
3. It should find GSPCA Source.  That's the source code for the driver. 
4. Install gspca-source.  It will also want to install something called the "Module Assistant".  This is like a driver compiler wizard.  

5. after those are installed, quit synaptic, and open the terminal.

sudo m-a prepare  

this sets up the module assistant.

sudo m-a a-i gspca    

this compiles and installs the driver.

unplug your webcam and plug it back in again, then open camstream.  

if no joy, look at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html), there are lists there of supported webcams, you could see if yours is on there.  they have instructions on how to figure out what your webcam is, too, because webcam makers are notoriously cryptic.

---

### Post by Noodels on 2007-09-30
I've been doing some research in the mean time and I managed to find Camorama, although the colour does not seem too good (proved in attachment) even after fiddling with those dial things.

Also I really want to get Ekiga softphone working but it does not pick up, even though Camorama just about works. If I install the driver mentioned should Ekiga softphone work?

---

### Post by Noodels on 2007-09-30
Okay, it seems ekiga is picking up the webcam, but I can't access the webcam's microphone. Any ideas?

---

