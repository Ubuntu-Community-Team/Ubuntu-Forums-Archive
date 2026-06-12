---
title: "Creative Live! Cam (Model VF0420)"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by CheetahCat on 2007-12-22
Hey fellas,

I searched the forums and found some threads about this specific webcam; unfortunately it seems that they changed the hardware specification - that's why I start a new thread.

Recently I bought a new webcam - a Creative Live! Cam/Vista IM. The model number is VF0420 and it shows up in lsusb as follows:

Bus 001 Device 004: ID 041e:4064 Creative Technology, Ltd

To install it I tried compiling a driver from source and easycam1 and 2. Nothing worked.

Does someone have an idea what chipset is used in these cams and which driver would be the proper one for it?

I am running Ubuntu Gutsy 7.10.

Thanks in advance!

Cheetahcat

---

### Post by CheetahCat on 2007-12-22
After opening the cam and checking the chip model I got it working by doing this:

sudo apt-get install subversion
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-2.6.20-16-386
make
sudo make install
sudo modprobe ov51x-jpeg

This basically compiles the needed V4L kernel module and provides access to the camera.

The camera works in Ekiga Softphone and VLC seamlessy; unfortunately Skype gives me a black video preview and Camorama repeats the video image 3 times horizontally. What can cause this? Anyone has an idea how to fix it?

Cheetahcat

---

