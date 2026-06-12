---
title: "Creative WebCam Live! Motion"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by JRaz on 2006-08-31
I did a search but I couldn't find any installation guides for this cam. Basically when I go to Camorama it says the device could not be found however when i type lusb into terminal it list the webcam and it even shows up under device manager.

So i am after help with two specific problems, firstly how to install drivers for this camera and secondly (which a doubt exists) a program to pan and tilt this camera.

---

### Post by Gaute65 on 2006-09-03
I also need help. I cant find any driver to this camera. 

When I type lsusb I got this information: 

Bus 003 Device 002: ID 041e:4041 Creative Technology, Ltd

Is there anybody that can help?

---

### Post by JRaz on 2006-09-03
I can confirm that I get the same code when I type lsusb;

Bus 001 Device 005: ID 041e:4041 Creative Technology, Ltd

---

### Post by Ice1532 on 2006-09-16
same here i get the same message... has anyone found a solution??

---

### Post by Ice1532 on 2006-09-17
i tried using spca55xx and it wont install correctly... it says some folder doesnot exist when i use the make comand

---

### Post by pcfreak on 2007-01-10
I also have this cam, and I also get the same when running lsusb:

Bus 003 Device 002: ID 041e:4041 Creative Technology, Ltd

I have been able to install the driver (I think), and it doesn't work, but if you look at the list at [http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html") you will find Creative WebCam Live!, however you will not find Creative WebCam Live! Motion, so, from what I know there is no linux driver avalible for this camera...

---

### Post by jokker on 2007-10-05
Is there any news about this issue ? After almost a year I believe there must be a driver out there ...

---

### Post by prjthompson on 2008-01-03
There must be someone smart enough to make it work?

---

### Post by jokker on 2008-01-05
There is a driver project for our camera, it's [here]("http://gkall.hobby.nl/sq930x.html")
It is in the early stage but the team is working on it, it works after compiling all the needed stuff they provide :popcorn:

---

### Post by prjthompson on 2008-01-16
is there an idiots guide to making the driver work?

---

### Post by OpenSourceDave on 2008-02-29
Also in need of a simple howto, please!

---

### Post by jimssi on 2008-03-27
i need guide too :confused:

---

### Post by Bob Unitt on 2008-03-27
And me - pretty please...

---

### Post by OpVines on 2008-05-30
Why hasn't anyone answered us?????

---

### Post by vixmusic01 on 2008-06-18
Hi Fellow Creative Live Motion Owners,

I do not feel competent to compile kernels etc myself.

I found these "How to pages" but I still can't figure it out.

Maybe someone here can do better and help us.

Let me know if you get it to work.

Victoria


[http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#DEV-MANUAL](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#DEV-MANUAL)

[http://www.linux.com/feature/118896](http://www.linux.com/feature/118896)

[http://linuxplanet.com/linuxplanet/tutorials/6463/2/](http://linuxplanet.com/linuxplanet/tutorials/6463/2/)

[http://exploits.org/v4l/](http://exploits.org/v4l/)

[https://help.ubuntu.com/community/Webcam#head-1dfc8ed1ffc06f00ed45b0696fa0b27948954058](https://help.ubuntu.com/community/Webcam#head-1dfc8ed1ffc06f00ed45b0696fa0b27948954058)

Example:

Manual installation instructions
Installing spca5xx manually

You can find howto's for manual installation of the spca5xx driver here.
Installing ov51x manually

You can find howto's for manual installation of the ov51x driver here.
Installing ov51x-jpeg manually

This is a hacked driver by [WWW] [http://www.rastageeks.org/](http://www.rastageeks.org/) and more info is available at [WWW] [http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page](http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page) Suported hardware [WWW] [http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams](http://www.rastageeks.org/ov51x-jpeg/index.php/Working_Webcams) My webcam is a Creative Live! Cam Vista IM and I found the instructions ready to go on the wiki very good. Installed it in 30 seconds
Installing UVC manually

The UVC module is included in 7.10, and possibly earlier but the included version has problems with some webcams. If you need to install/update it you can find a howto here
Edgy troubleshooting : pwc driver is broken

On Edgy, the pwc driver in the kernel is [WWW] broken.

[WWW] List of the working webcams with pwc.

An easy check to see if your pwc driver is broken :

$ lsmod | grep pwc 

pwc 51964 1  <- Your driver is broken ! (around 50kb)

pwc 93984 0  <- your driver seems ok. (around 90kb)

How to get your webcam working ?

1) Install build-essential and the kernel-headers for your kernel (linux-headers-2.6.17-6-686 for me).

2) Download latest driver from [WWW] [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) ([WWW] [http://www.saillard.org/linux/pwc/files/pwc-10.0.12-rc1.tar.bz2](http://www.saillard.org/linux/pwc/files/pwc-10.0.12-rc1.tar.bz2) for me)

3) Unpack and go into extracted directory

4)

make

5)

sudo modprobe -r pwc

6)

sudo cp pwc.ko /lib/modules/`uname -r`/kernel/drivers/media/video/pwc/pwc.ko.saillard

7)

cd /lib/modules/`uname -r`/kernel/drivers/media/video/pwc

8)

sudo mv pwc.ko pwc.ko.ubuntu

9)

sudo ln -s pwc.ko.saillard pwc.ko

10)

sudo depmod -a

11)

sudo modprobe pwc

12) Enjoy! :)
See also

* InstallingLogitechQuickcamPro5000OnEdgy

* [WWW] Installing the Eyetoy as a Webcam with Kopete

* [WWW] Using a USB Webcame to capture videos for upload to YouTube

CategoryDocumentation CategoryCleanup

---

### Post by pittu_00 on 2008-06-25
I followed the instructions given on the website to download the sq930x driver for the Creative Live Motion but I am not geting the /dev/video file. I tried doing modprobe sq930x but that gives an error 
FATAL : sq930x module not found. 

Can anyone guide me whats wrong ?

---

