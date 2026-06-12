---
title: "Installing UVC on 9.10 (webcam 0402:5606)"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Altu13 on 2009-11-22
Hi there. First of all sorry for my english. 
I was looking for and i find them, some solutions about installing an BisonCam (Webcam) on the lastest Ubuntu.

I need comment that my ubuntu is a new, clear and complete installation, with the lastest updates.

For specifications, my webcam is a BisonCam (comes with Clevo Notebook, not drivers for anything than win XP and VISTA comes).

The lsusb says:

> Bus 001 Device 003: ID 0402:5606 ALi Corp. USB 2.0 Camera(perfect, it's supported exactly by UVC, as says [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/))

Without anything more than the first installation, webcam is recognized but seems everything black, as its state is off. 

So, i downloaded the camera monitor and it's on. Same result. Im using GUVCVIEW to probe it. Also amsn.

So i try to install the lastest svn of UVC and get the error about the change of repository to linuxtv.org when i do the make command.

> -------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------In other ways, i actualice the headers and something else what i need (as i read in other 200 forum's post). Actually im working on:

2.6.31-14-generic

Also i installed the m-a and use it instead the aptitude but a search of linux-uvc says: What re u talking about, willys?

So... my question is...

can anybody with experience on this or kwnoledge about that or anything that wants to helpme in there (any ideas will be preciated) please give me a solution step by step
about:

1) how to download, install and compile the lastest UVC to try it.
2) resolve if the issues of this problem is something else i dont considereer, maybe the black screen is for something else.

Yes, the webcam works, at least in windows....

Thanks a lot for any reply or help

Leandro ;)

---

