---
title: "Got a Microsoft LifeCam VX-6000 webcam?"
date: 2008-11-25
forum: Multimedia Software
---

### Post by forkandles on 2008-11-25
Got a Microsoft LifeCam VX-6000? Try this.
**There is no guarantee that this will make the MS LifeCam VX-6000 work in Linux but it is a good starting point.**

Please report back with your experiences. If anybody has managed to get it working via another route please let us know.
Before you start, make sure the LifeCam is plugged in DIRECTLY to one of your computer's USB ports and not via a USB hub.

Typing lsusb in terminal, as normal user ($), should produce something like this:

Bus 006 Device 005: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000

The LifeCam VX-6000 is made by Microdia.

In terminal, as super user (#), copy and paste this:

sudo apt-get update && apt-get install linux-headers-$(uname -r) git-core git-gui

Now as normal user ($) type:

cd /home/myusername/Downloads (OR a similar location e.g. Desktop or NewFolder)

Then create a folder called microdia which contains all the source code by typing in terminal, as normal user ($):

git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

cd microdia
make

Then as super user (#) type:
sudo insmod ./microdia.ko

If everything works fine you won't see any message on stdout, but your dmesg will have lines like the following:
microdia: Microdia USB2.0 webcam driver startup
microdia: Microdia USB2.0 Webcam - Product ID 6260.
microdia: Release: 0100
microdia: Number of interfaces : 1
microdia: Microdia USB2.0 Camera is now controlling video device /dev/video0
usbcore: registered new interface driver usb_microdia_driver
microdia: v0.0.0 : Microdia USB Video Camera
So, congratulations! Your webcam is ready for action now. If not:
Troubleshooting insmod errors 
# insmod microdia.ko
insmod: error inserting 'microdia.ko': -1 Unknown symbol in module
*See the output of #dmesg
the last few lines would be complaints about missing symbols, depending upon whats missing.*
You may not have loaded the modules that module depends on,
So it failed with those error messages. You would need to modprobe for that module's dependencies.
*
Try
$ sudo modprobe videodev
$ sudo modprobe compat-ioctl32
then
$ sudo insmod microdia.ko
*If still you get errors on #insmod,
perhaps you have had a recent kernel update. 
*
Update a the lists the dependencies for every module (*see below for alternative).
$ sudo depmod -a*
$ sudo m-a update,prepare
You may also need to regenerate kernel initrd image (really).
*
insmod: error inserting './microdia.ko': -1 Invalid module format 
*
Possible Reason*
"The gcc which compiled the kernel and*
the gcc which compiled the module are incompatible."*
Possible Solution
Install an older gcc side-by-side, and change cc environment variable to use older version.*
*
FIXME: more possibilities
6. Test it using*mplayer
$*mplayer*tv://*-tv*driver=v4l2:width=640:height=480:fps=25:device=/dev/video0*-vo*x11
7. Installing the Microdia Driver
This step is optional. If you don't do it though you will have to insmod microdia.ko everytime you reboot.

$ strip -g microdia.ko
$ sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
$ sudo depmod -a 
*updated with 
sudo m-a update,prepare 
depmod -a 

make: *** [driver] Error 127 
error 127 simply means that the module is not in the proper location, 
not a major error. 

With thanks to:
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Good luck.

---

### Post by amp0303 on 2008-12-18
I'm a complete noob when it comes to Linux but how do you change from normal user ($) to superuser (#)?

---

### Post by victorbstan on 2009-08-15
sudo <etc> 

usually does it (temporarily)

or just look for the root terminal somewhere under the customize application menu in Ubuntu

or try gksu

---

### Post by victorbstan on 2009-08-15
PS.

Anyone got this cam to work properly? I am in need of a very high quality web cam... 

> **forkandles said:**
> Got a Microsoft LifeCam VX-6000? Try this.
**There is no guarantee that this will make the MS LifeCam VX-6000 work in Linux but it is a good starting point.**

Please report back with your experiences. If anybody has managed to get it working via another route please let us know.
Before you start, make sure the LifeCam is plugged in DIRECTLY to one of your computer's USB ports and not via a USB hub.

Typing lsusb in terminal, as normal user ($), should produce something like this:

Bus 006 Device 005: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000

The LifeCam VX-6000 is made by Microdia.

In terminal, as super user (#), copy and paste this:

sudo apt-get update && apt-get install linux-headers-$(uname -r) git-core git-gui

Now as normal user ($) type:

cd /home/myusername/Downloads (OR a similar location e.g. Desktop or NewFolder)

Then create a folder called microdia which contains all the source code by typing in terminal, as normal user ($):

git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)

cd microdia
make

Then as super user (#) type:
sudo insmod ./microdia.ko

If everything works fine you won't see any message on stdout, but your dmesg will have lines like the following:
microdia: Microdia USB2.0 webcam driver startup
microdia: Microdia USB2.0 Webcam - Product ID 6260.
microdia: Release: 0100
microdia: Number of interfaces : 1
microdia: Microdia USB2.0 Camera is now controlling video device /dev/video0
usbcore: registered new interface driver usb_microdia_driver
microdia: v0.0.0 : Microdia USB Video Camera
So, congratulations! Your webcam is ready for action now. If not:
Troubleshooting insmod errors 
# insmod microdia.ko
insmod: error inserting 'microdia.ko': -1 Unknown symbol in module
*See the output of #dmesg
the last few lines would be complaints about missing symbols, depending upon whats missing.*
You may not have loaded the modules that module depends on,
So it failed with those error messages. You would need to modprobe for that module's dependencies.
*
Try
$ sudo modprobe videodev
$ sudo modprobe compat-ioctl32
then
$ sudo insmod microdia.ko
*If still you get errors on #insmod,
perhaps you have had a recent kernel update. 
*
Update a the lists the dependencies for every module (*see below for alternative).
$ sudo depmod -a*
$ sudo m-a update,prepare
You may also need to regenerate kernel initrd image (really).
*
insmod: error inserting './microdia.ko': -1 Invalid module format 
*
Possible Reason*
"The gcc which compiled the kernel and*
the gcc which compiled the module are incompatible."*
Possible Solution
Install an older gcc side-by-side, and change cc environment variable to use older version.*
*
FIXME: more possibilities
6. Test it using*mplayer
$*mplayer*tv://*-tv*driver=v4l2:width=640:height=480:fps=25:device=/dev/video0*-vo*x11
7. Installing the Microdia Driver
This step is optional. If you don't do it though you will have to insmod microdia.ko everytime you reboot.

$ strip -g microdia.ko
$ sudo cp microdia.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
$ sudo depmod -a 
*updated with 
sudo m-a update,prepare 
depmod -a 

make: *** [driver] Error 127 
error 127 simply means that the module is not in the proper location, 
not a major error. 

With thanks to:
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Good luck.

---

### Post by wafflcommish on 2009-08-27
When I try to run the "Make" command, I get the following: 
make -C /lib/modules/2.6.28-15-server/build SUBDIRS=/home/brian/Desktop/microdia modules
make: *** /lib/modules/2.6.28-15-server/build: No such file or directory.  Stop.
make: *** [driver] Error 2

Any thoughts would be welcome.

---

### Post by ghuiber on 2009-09-19
Not me. I tried, and got a segmentation fault right after this part:
> Need to get 0B/3482kB of archives.
After this operation, 7918kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
In addition, I had to chmod all sorts of files and folders to at least 770 as I went along.

---

### Post by qwelm on 2009-09-22
I got all the way to the insmod step and it is telling me there is no ./microdia.ko.  Suggestions?

---

### Post by wafflcommish on 2009-09-22
When I run the make command, I get the following:

make -C /lib/modules/2.6.28-15-server/build SUBDIRS=/home/brian/Desktop/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-server'
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-usb.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-v4l2.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-sysfs.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-dev.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-queue.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-bridge.o
  CC [M]  /home/brian/Desktop/microdia/omnivision.o
  CC [M]  /home/brian/Desktop/microdia/micron.o
  CC [M]  /home/brian/Desktop/microdia/hv7131r.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-debugfs.o
  LD [M]  /home/brian/Desktop/microdia/sn9c20x.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/brian/Desktop/microdia/sn9c20x.mod.o
  LD [M]  /home/brian/Desktop/microdia/sn9c20x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-server'
make: ctags: Command not found
make: *** [ctags] Error 127

Any thoughts?

---

### Post by zorba_the_greek on 2009-09-26
> **qwelm said:**
> I got all the way to the insmod step and it is telling me there is no ./microdia.ko.  Suggestions?

exactly the same problem... :-k

---

### Post by gqpolo on 2009-09-29
> **wafflcommish said:**
> When I run the make command, I get the following:

make -C /lib/modules/2.6.28-15-server/build SUBDIRS=/home/brian/Desktop/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-server'
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-usb.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-v4l2.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-sysfs.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-dev.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-queue.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-bridge.o
  CC [M]  /home/brian/Desktop/microdia/omnivision.o
  CC [M]  /home/brian/Desktop/microdia/micron.o
  CC [M]  /home/brian/Desktop/microdia/hv7131r.o
  CC [M]  /home/brian/Desktop/microdia/sn9c20x-debugfs.o
  LD [M]  /home/brian/Desktop/microdia/sn9c20x.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/brian/Desktop/microdia/sn9c20x.mod.o
  LD [M]  /home/brian/Desktop/microdia/sn9c20x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-server'
make: ctags: Command not found
make: *** [ctags] Error 127

Any thoughts?
Take a look at [this]("http://groups.google.com/group/microdia/web/testing-microdia-driver-draft") site it says that error 127 isn't a major problem. Look at section 3 and the part after section 4. It has to do with the module not being in the right location. I hope you get it working. I'm getting error code 2. Good Luck!!!

---

