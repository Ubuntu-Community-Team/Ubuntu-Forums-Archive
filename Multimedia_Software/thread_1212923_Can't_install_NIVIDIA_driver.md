---
title: "Can't install NIVIDIA driver"
date: 2009-07-14
forum: Multimedia Software
---

### Post by meschaefer on 2009-07-14
I have been having a problem installing the newest
NIVIDIA driver.   When I installed versions 173 and 180, it gave me real problems causing my system to freeze up when I opened firefox or XBMC.  I uninstalled to drivers and went back to the open source drivers, and then tried to install 185.19

After downloading the driver, I went into terminal and used the command

sudo pkill X

After I stopped the X server, I ran the download from NVIDIA from terminal

sudo install  NAME OF DRIVER

I then get the following error

install;  missing destination file operand after

I am running a GIGABYTE mother board with an intergrated GEOFORCE 9400
Video out via HDMI
Intel Core Duo 2.8
Ubunto 9.04

---

### Post by j7%&lt;RmUg on 2009-07-14
Ok first of all the open source drivers should be good enough, im running and 8500GT on the open source 180 drivers.

Second of all there is no such command in ubuntu as "sudo install NAME OF DRIVER".

That isnt going to get you very far.

So, i take it you downloaded the 185 drivers from the nvidia website? All i did to get my 8500GT working was to go to System > Preferences > Appearance, then go to the Visual Settings tab and check extra effects, it should then prompt you to install the 180 nvidia drivers accept this and wait for it to finish. then reboot and you should be good to go.

EDIT: I also just found this guide in another section of the forums:

This guide may or may not work for you, the author of it does say that he doesnt know if it works for a 9400 but its worth a try if you really do need the 195.18 drivers.

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

### Post by meschaefer on 2009-07-14
> **nisshh said:**
> Ok first of all the open source drivers should be good enough, im running and 8500GT on the open source 180 drivers.

Second of all there is no such command in ubuntu as "sudo install NAME OF DRIVER".

That isnt going to get you very far.

So, i take it you downloaded the 185 drivers from the nvidia website? All i did to get my 8500GT working was to go to System > Preferences > Appearance, then go to the Visual Settings tab and check extra effects, it should then prompt you to install the 180 nvidia drivers accept this and wait for it to finish. then reboot and you should be good to go.

If you need me to be specific,  the command was 

sudo install NVIDIA-Linux-186.18.14-pkg1.run

(i was trying to avoid spelling out he name of the driver, my bad)

When I do so, I get the following error

install;  missing destination file operand after `NVIDIA-Linux-186.18.14-pkg1.run

I was able to load up the 180 driver, but it caused my system to freeze up.  So I want to give the 185 driver a try to see if it solved some of my problems.

---

### Post by DominicF on 2009-07-14
Hi,

I've been updating drivers today on my system.  You might find it usefull to follow these instructions:

[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)

I managed to install the 185.18.14 drivers but I have an issue when I connect via hdmi as the image on my LCD TV looks oversized i.e. the ubuntu desktop menus are top and bottom are not visable but are present.  But connecting to VGA to VGA of the LCD TV everything works nicely.  I'd like to know if you experience the issue with HDMI.

---

### Post by meschaefer on 2009-07-14
> **DominicF said:**
> Hi,

I've been updating drivers today on my system.  You might find it usefull to follow these instructions:

[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)

I managed to install the 185.18.14 drivers but I have an issue when I connect via hdmi as the image on my LCD TV looks oversized i.e. the ubuntu desktop menus are top and bottom are not visable but are present.  But connecting to VGA to VGA of the LCD TV everything works nicely.  I'd like to know if you experience the issue with HDMI.


I havn't had a chance to review that thread, but the thread recommended before that was the one I had been using in the first place.

As to your problem, that is because the TV is over scanning.  i.e. it scan's part of the picture off of the screen.  Many TVs doe this with HDMI/DVI signals but not VGA.  I fixed this  through a setting on the TV.

---

### Post by meschaefer on 2009-07-15
> **DominicF said:**
> Hi,

I've been updating drivers today on my system.  You might find it usefull to follow these instructions:

[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)



 I am not ready to call this issue solved, but I have fixed my problem.

I used the information found in the link above, but still ran into the same error:

install:  missing destination file operand after `NVIDIA-Linux-186.18.14-pkg1.run

At this point I figured that it would just be easier to try a fresh install of Ubuntu since this was a new computer and it this was becoming extremely frustrating. 

After a fresh install, I followed the above referenced thread and was able to load up the driver without a problem. 

Thanks for everybody's help

Matt

---

### Post by mavis311 on 2009-07-15
> **DominicF said:**
> Hi,

I've been updating drivers today on my system.  You might find it usefull to follow these instructions:

[http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/)


Wow, that page is so very useful.  I just installed ubuntu for the first time yesterday.  I followed the instructions on this page and they worked wonderfully!  Only problem, X didn't start up in 800x600.  It started up in 1280x1024!  I was never able to run this resolution under windows!  I'm thrilled!

---

