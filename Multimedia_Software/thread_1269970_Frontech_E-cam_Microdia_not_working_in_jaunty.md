---
title: "Frontech E-cam Microdia not working in jaunty"
date: 2009-09-18
forum: Multimedia Software
---

### Post by MikeMiracle on 2009-09-18
Make &#8211; Frontech E-Cam (Gem)
 Model &#8211; JIL -225
 Country Of Origin- China
 

 

 uname -r
 

 2.6.28-15-generic   (Ubuntu jaunty)
 

 lsusb
 

[html]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 0c45:614a Microdia  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
[/html] **The problem**
 

 No /dev/video* is created.
 

 I have tried following 3 approaches
 

 **Approach 1**
 

 Installed microdia driver as per instructions from [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)
 

 Still /dev/video* is not created.
 

 Seems the Webcam is not supported yet with microdia driver.
  
 **Approach 2**
 

 The webcam driver CD has a directory named Linux drivers . Initially thought that this will be useful.
 It has 2 files in it ie , linux_120snxcam.o and snxcam.o . tried insmod . But looks like .o extension is no longer supported by new kernels. I am not sure of any way to make the webcam work from these files.
 

 **Approach3**
 

 Tried ndiswrapper . Read some where that it can be used for non wireless drivers also . But after installing the driver , The GUI for ndiswrapper says No hardware present.
 

 

 Seems the Webcam is not supported yet on Ubuntu .  Comments please.

---

### Post by ProfBib on 2009-09-27
After reading (Amazon.com user comments) that several people had success in making my variant of this webcam working in Hardy, I went ahead and purchased one.

Unfortunately, I am having the exact same difficulties with it on my Jaunty installation.:(

---

### Post by g0ng on 2009-10-20
any progress on this?

I have the crypto budget III camera

---

### Post by justborn on 2009-10-28
i think ur issue is fixed in karmic koala.

so u should try it on karmic.

for best results try it out on a fresh install of karmic,rather than an upgrade.9.10 rox!:D

---

### Post by MikeMiracle on 2009-10-30
Little luck still with karmic upgrade.tried with cheese and Skype. Can't afford a fresh install. Any pointers to get it working on the upgrade.

---

### Post by no2498 on 2009-10-31
try running gstreamer-properties in the terminal
click video try diff settings

---

### Post by MikeMiracle on 2009-10-31
Had tried  gstreamer-properties. Not working.

There is no /dev/video0.

Any pointers to debug?

---

### Post by Irtsi on 2009-11-12
The camera worked perfectly on Cheese and Skype with Xubuntu 9.10 but it's not working with Ubuntu 9.10 at all.

---

### Post by astarr on 2010-07-29
Also having this problem.  Mine is a "crystal cam" and appears as 0c45:614a Microdia after using lsusb.

---

### Post by no2498 on 2010-07-29
astarr
look in add/remove see if gstreamer good,bad,ugly,and 10 is installed


gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by sebin on 2012-07-12
No update on this issue? What i understood by this is, Frontech E-cam not supported by Ubuntu?

---

