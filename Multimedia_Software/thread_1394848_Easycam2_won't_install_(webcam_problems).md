---
title: "Easycam2 won't install (webcam problems)"
date: 2010-01-31
forum: Multimedia Software
---

### Post by thedutchrockstar on 2010-01-31
Dear ubuntuforums users,
You guyz have helped me in so many ways, and I seriously thought that there was a solution for every problem on this formu, but allas I have a new one...
So the problem goes that I have a webcam (Trust 16430 [Chat Webcam]) that just doesn't seem to work.
Now according to multple guides I simply have to install easycam2 to find the drivers and install the cam.
There lies another problem, easycam2 is giving me a hard time... it just won't install.
Now here is what I do in the terminal:

vincent@vincent-desktop:~$ sudo apt-get install easycam2-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-gtk: Depends: python2.4-glade2 but it is not installable
                Depends: python2.4-gtk2 but it is not installable
                Depends: easycam2-core but it is not going to be installed
E: Broken packages

so then I try:

vincent@vincent-desktop:~$ sudo apt-get install easycam2-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  easycam2-core: Depends: python-xml but it is not installable
E: Broken packages

Not giving up with :

vincent@vincent-desktop:~$ sudo apt-get install python-xml
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-xml is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-xml has no installation candidate

And then I am stuck.
so quick rehab on what I have
Ubuntu 9.10 32bit
Trust webcam16430

Maybe someone has a different way of getting the driver or installing easycam2?
Awaiting your loving help
Vincent

---

### Post by thedutchrockstar on 2010-02-04
Anyone? please?
:confused:

---

### Post by ubt_user_0331 on 2010-02-04
Is it really necessary to use easycam? The ubuntu generic driver works well with many webcams, try installing cheese.
(sudo apt-get install cheese) and see if the cam works.
You might (or might not) need to execute 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese &

---

### Post by thedutchrockstar on 2010-02-04
> **ubt_user_0331 said:**
> Is it really necessary to use easycam? The ubuntu generic driver works well with many webcams, try installing cheese.
(sudo apt-get install cheese) and see if the cam works.
You might (or might not) need to execute 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese &

Hey thanks for the reply,
unfortunately the generic driver doesn't seem to support my webcam.
I have downloaded cheese before with little result, I see a loading screen, my webcams lights up but after a few seconds turns off again and I get a tv like screen.
Canorama gets stuck when trying to load my webcam and so does Amsn, skype doesn't seem to manage it either... and other ideas?
thnkx

---

### Post by no2498 on 2010-02-05
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each
if it comes on try cheese

---

### Post by thedutchrockstar on 2010-02-06
> **no2498 said:**
> open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each
if it comes on try cheese

Thank you for responding, but you help came to no avail,
I have however found some extra info which might help you guyz help me decode and resolve the problem:

this is what I get for the webcam when typing in the terminal lsusb

Bus 002 Device 003: ID 0c45:613e Microdia PC Camera (SN9C120)

now if that helps anyone... PLEEAAASE respond =D
Many thanks in advance

---

### Post by ubt_user_0331 on 2010-02-11
I saw that your camera is Microdia and found this
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)
Maybe this driver will help?
I do not have a similar camera so cannot test the installation instructions though

---

### Post by Bluebris on 2010-03-12
> **no2498 said:**
> open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each
if it comes on try cheese

  When i open gstreamer properties, the second option on video (when i click on test) shows the camera ok. If i open cheese using the line LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese & as advised above, i can see the camera ok...but in other applications i can't get it to work, and they're really the whole reason i got the camera in the first place!  Please HELP!!

---

### Post by no2498 on 2010-03-12
you need to do the preload for every program

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so you type program name here

---

### Post by thedutchrockstar on 2010-03-18
Okay so I have decided to buy a linux ready camera...
better than my old one,
So I regard this topic as closed
but thank you EVERYONE
who tried to help me,

you guyz are awesom :KS

---

### Post by no2498 on 2010-03-18
you must like spilled milk
we had the cam working is all it takes for us to work with
send me the old 1 i have 7 more computers with out 1
enjoy your new cam

---

### Post by thedutchrockstar on 2010-03-22
I just wanted to let everyone no I did manage to get the webcam working again,
The problem was that it wasn't working with the drivers of the gspca,
But recently they released a new set of test drivers which included my webcam :D
but I am new to this forum so how do I get the solved message up there?

thanks for the help guys!
and thanks for the kick in my lazy *** no2498, you made me take a good look again ;)
:KS

---

