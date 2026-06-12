---
title: "Microdia/Trust-Webcam won't work"
date: 2010-01-21
forum: Multimedia Software
---

### Post by manoriax on 2010-01-21
Hey,

I've just bought a new, cheap webcam. The manufacturer is "Trust", who builds chips of Microdia in their products. So, I plugged my new webcam, noticed that the driver obviously is missing and I finally decided to use Google.

Well, there were some tutorials which include manual installation of gspca (which should be included in the recent kernel files, but somehow isn't). So..I tried the manual installation and it aborts with the message, that there was some error in one of the code files..however.

I continued searching for a solution and found it on the German Ubuntu community page, ubuntuusers.de. Their wiki says that I have to run the following commands that download and compile the right drivers for my webcam. Or at least they should do so.

```
sudo apt-get install git-core gitk git-gui git-doc curl
``````
git clone http://repo.or.cz/r/microdia.git 
``````
cd microdia
``````
make
``````
sudo modprobe videodev
``````
sudo modprobe compat-ioctl32
``````
sudo insmod sn9c20x.ko 
```...and eventually it should work properly. So far the theory. In fact it aborts at exactly this point:
```
sudo modprobe compat-ioctl32
```and gives the following error message:
```
phil@phil-desktop:~/microdia$ sudo modprobe compat-ioctl32
FATAL: Module compat_ioctl32 not found.

```Well, urm. I guess I'll have to install that missing module..somehow, but I do not really have hunch.

Thanks for reading, I'm looking foward to reading a solution. :)

Regards

---

### Post by manoriax on 2010-01-22
No ideas? :/

---

### Post by ukko on 2010-01-24
Hi, **manoriax**

I have a simmilar trouble with webcam.

I found on Arch Linux forum this  phrase:

> The module compat-ioctl32 was not found but that doesn't matter as that is only required for 64bit systems.

[url]

May be it is not need.

---

### Post by thedutchrockstar on 2010-02-07
Hey I have the same problem,
but like said the compay file is not necessary!
still in installed the sn9c20x.ko, and now in cheese it won't even find my cam =S

---

### Post by manoriax on 2010-02-07
Has anyone got the cam with HWID 0c45:6142 to work? ^^

---

### Post by ukko on 2010-02-07
> **manoriax said:**
> Has anyone got the cam with HWID 0c45:6142 to work? ^^

No :(

---

### Post by no2498 on 2010-02-07
try getting ( wxcam )
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
hope this helped 
odd things go on with cheese
1 day it opens  next day it dont
save the ( gstreamer-properties ) if the cam stops working you need to run it again 
an open cheese look at its faq's in help

---

### Post by adlerhn on 2010-02-11
AFAIK, the 0c45:6142 webcam is not (yet) supported in the gspca driver. In the kernel source code (drivers/media/video/gspca/sonixj.c) there is a line for this device, but it is commented.

Most likely nobody has had time or the chance to test this entry yet.

---

### Post by manoriax on 2010-02-13
Well, urm, I'm absolutely interested in testing it, if someone tells me how.

---

### Post by manoriax on 2010-03-20
We have managed to implement the webcam to the latest testing version of gspca.

---

### Post by adlerhn on 2010-03-22
Testing version available from [http://moinejf.free.fr/]("http://moinejf.free.fr/").

The fix should also be included in Linux kernel 2.6.35.

---

### Post by zmeuka on 2010-07-09
I've got a Hama AC-150 webcam with HWID same as above. 
Works fine with the test package (2.9.50). Thank you!

---

