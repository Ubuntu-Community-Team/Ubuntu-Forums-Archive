---
title: "Webcams for ubuntu?"
date: 2010-02-27
forum: Multimedia Software
---

### Post by indiana_crook on 2010-02-27
Does anyone know of any good webcams that I can use with ubuntu 8.04 and up?  I'm having trouble with compatibility on many webcams.

---

### Post by indiana_crook on 2010-02-27
Anybody??

---

### Post by 2hot6ft2 on 2010-02-27
Logitech Quickcam Orbit or Sphere
My reason is that they work with motion so they can double as security cams in ubuntu.
[MotionGuideInstallation#Supported_Hardware]("http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation#Supported_Hardware")

NOT the quickcam for notebooks though. I picked one up for about $5 and it wouldn't work with motion.

---

### Post by indiana_crook on 2010-02-27
> **2hot6ft2 said:**
> Logitech Quickcam Orbit or Sphere
My reason is that they work with motion so they can double as security cams in ubuntu.
[MotionGuideInstallation#Supported_Hardware]("http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideInstallation#Supported_Hardware")

NOT the quickcam for notebooks though. I picked one up for about $5 and it wouldn't work with motion.

I'll try one... Thank you!

---

### Post by no2498 on 2010-02-27
plug in most all web cams and they work old or new

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom tets button for each 1

now get a program to see-use it with
like cheese or wxcam

---

### Post by 2hot6ft2 on 2010-02-27
> **indiana_crook said:**
> I'll try one... Thank you!
You're welcome. In addition to cheese as was posted xawtv is a good way to check web cams. It's in the repos.

---

### Post by karrank% on 2010-02-28
Using a Logitech QuickCam Communicate STX on a custom budget build, amd 780g board, running 8.04 works fine for Skype.

---

### Post by indiana_crook on 2010-03-03
> **no2498 said:**
> plug in most all web cams and they work old or new

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom tets button for each 1

now get a program to see-use it with
like cheese or wxcam

I tried all this and still not working.  It says the following:

"Video for Linux (v4l): Device "/dev/video0" does not exist."

Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

---

