---
title: "Built in laptop web cam not working?"
date: 2011-03-24
forum: Multimedia Software
---

### Post by demonic_crow on 2011-03-24
I have ubuntu 10.10 64 bit install on my HP DV6700 laptop.  I can't get the webcam to work on it at all.  I try the gstreamer-properties and nothing work there.  I also tried the cheese device and doesn't find it.  When I run guvcview it say make sure the driver is install.  Anyone know what I need to install?

---

### Post by Script Warlock on 2011-03-24
lsmod | grep videodev

---

### Post by demonic_crow on 2011-03-24
Doesn't do anything when I type that in.

---

### Post by maddbaron on 2011-03-24
if your using gstreamer


 type ```
gstreamer-properties
```  in terminal and go to video, see if your webcam is selected in default input.  The driver should also be video for linux 2... then run test from default input if nothing go to default output and try x window system (no xv) or use the x11 setting then close once u see video. 
 

I had the same issue that fixed in almost everything (my skype doesn't work)

Read too quickly, are you sure your gstreamer codecs are installed completely?  try reinstalling them

---

### Post by Script Warlock on 2011-03-24
did you update your machine?

---

### Post by demonic_crow on 2011-03-25
> **maddbaron said:**
> if your using gstreamer


 type ```
gstreamer-properties
```  in terminal and go to video, see if your webcam is selected in default input.  The driver should also be video for linux 2... then run test from default input if nothing go to default output and try x window system (no xv) or use the x11 setting then close once u see video. 
 

I had the same issue that fixed in almost everything (my skype doesn't work)

It doesn't show any device connected.  I tried the x window system and it just show a test video with color strip and stuff but still doesn't do anything for me.  It also say it can't identify device 'dev/video0'.  Also get this after I run gstreamer-properties:

```
$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'


```

---

### Post by demonic_crow on 2011-03-25
> **Script Warlock said:**
> did you update your machine?

This is a fresh install of Ubuntu 10.10 64 bit.  Didn't upgrade from anything if that matter.  Also my computer have the latest update too.

---

### Post by Script Warlock on 2011-03-25
maybe try compile the uvc driver lets see if it works on your machine before that let us see your lsusb output.

---

### Post by demonic_crow on 2011-03-25
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Script Warlock on 2011-03-25
its outdated but just a reference for your hp... [https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

---

### Post by demonic_crow on 2011-03-25
Thanks I will check that out and report back to what happen.

---

### Post by no2498 on 2011-03-25
have you did this yet

sudo apt-get install ubuntu-restricted-extras

---

### Post by demonic_crow on 2011-03-25
Nothing on that site helped me out.  [I] Even this didn't work at all:  

"got the webcam to work (on Debian etch) by installing the packages:  **linux-uvc-tools**, **libpt-plugins-v4l2**, [B]linux-uvc-source"

[/B][/I][I]I couldn't even find those packet.  Also still when running  gstreamer it can't find the dev/video0.  So wondering what to do about  that.  I'm dual booting window 7 and its just crap.  HP offer the upgrade but the OS doesn't even support any driver for it not even the HP site.  GRRRRRRRRRRRRRRR

P.S.  Yes I have the restricted extra now installed.  Thought I did that before and it still doesn't help any.
[/I]

---

### Post by Script Warlock on 2011-03-26
if everything fails why not buy a good cheap usb webcam for your laptop..

---

### Post by Script Warlock on 2011-03-26
heres how to get the uvc try this:
apt-get install git
apt-get install patchutils

git clone git://linuxtv.org/media_build.git
cd media_build
./build.sh
make install

sudo depmod -a
luvcview (apt-get install luvcview if none)

goodluck...

---

### Post by demonic_crow on 2011-03-26
> **Script Warlock said:**
> if everything fails why not buy a good cheap usb webcam for your laptop..

I did end up buying a $20 web cam yesterday.  The reason why I want to get this to work cause I know it does work.  It did work in the past and now it doesn't for some odd reason.  If it can save me money on buying a webcam that be awesome and I wouldn't have to take it around with me. Thank you for helping me to get this to work.  Will report back to you here in a bit with your other instruction.

---

### Post by demonic_crow on 2011-03-26
> **Script Warlock said:**
> heres how to get the uvc try this:
apt-get install git
apt-get install patchutils

git clone git://linuxtv.org/media_build.git
cd media_build
./build.sh
make install

sudo depmod -a
luvcview (apt-get install luvcview if none)

goodluck...

This is what it says now:

$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
ERROR opening V4L interface: No such file or directory

Look like its getting closer to being fix.

---

### Post by demonic_crow on 2011-03-26
lsmod | grep uvc

Doesn't show anything.  I did a search for uvc and it does show it being in the 
lib/modules/2.6.35-28-generic/kernel/drivers/media/video

Edit:  Also I ran a search for 
v4l2_common
v4l1_compat
compat_ioctl32

and they aren't showing up.  From what this site says [http://www.quickcamteam.net/documentation/faq/unknown-symbols-on-load](http://www.quickcamteam.net/documentation/faq/unknown-symbols-on-load) I need it. Any thought on it.

---

### Post by Script Warlock on 2011-03-26
were getting closer run the tests

sudo modprobe -r uvcvideo
sudo modprobe uvcvideo

lsusb
ls /dev/video*
lsmod | grep videodev
gstreamer-properties

guvcview -d /dev/video0

---

### Post by demonic_crow on 2011-03-26
demonic@laptop:~$ sudo modprobe -r uvcvideo
demonic@laptop:~$ sudo modprobe uvcvideo
demonic@laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
demonic@laptop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
demonic@laptop:~$ lsmod | grep videodev
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
demonic@laptop:~$ guvcview -d /dev/video0
guvcview 1.4.1
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

---

### Post by Script Warlock on 2011-03-26
what interest me is this > demonic@laptop:~$ lsmod | grep videodev
videodev 49359 1 uvcvideo
v4l1_compat 15519 2 uvcvideo,videodev
v4l2_compat_ioctl32 12614 1 videodev

try loading this
modprobe videodev
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32

post the lspci result

and then retry the tests

---

### Post by demonic_crow on 2011-03-26
```
demonic@laptop:~$ modprobe videodev
demonic@laptop:~$ modprobe v4l1-compat
demonic@laptop:~$ modprobe v4l2-common
FATAL: Error inserting v4l2_common (/lib/modules/2.6.35-28-generic/kernel/drivers/media/video/v4l2-common.ko): Operation not permitted
demonic@laptop:~$ sudo modprobe v4l2-common
[sudo] password for demonic: 
demonic@laptop:~$ modprobe compat_ioctl32
FATAL: Module compat_ioctl32 not found.
demonic@laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

---

### Post by demonic_crow on 2011-03-26
After the test:
```
demonic@laptop:~$ sudo modprobe -r uvcvideo
demonic@laptop:~$ sudo modprobe uvcvideo
demonic@laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
demonic@laptop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
demonic@laptop:~$ lsmod | grep videodev
videodev               49359  2 uvcvideo,v4l2_common
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
demonic@laptop:~$ guvcview -d /dev/video0
guvcview 1.4.1
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
```

---

### Post by Script Warlock on 2011-03-26
your lsusb and lspci - webcam is not detected
test have similar outputs then its time to attach your newly bought external webcam :)

---

### Post by demonic_crow on 2011-03-26
So could it be possible that it got detach in the computer then or is it still a driver issue maybe?

Thanks for everything you have done.

---

### Post by Script Warlock on 2011-03-26
its an integrated cam it could be the driver. my niece acer one laptop has a defective webcam that i thought it was a driver issue but then after i tried to reinstall xp and win7(halfway of the installation it freezes) it failed to detect the webcam. we got success in ubuntu lucid installation but has no webcam also so after an hour of checking the cam actually is broken so i let him buy a new logitech usb webcam, but thats another story.

---

### Post by demonic_crow on 2011-03-26
ok cool, I will go ahead and check it all but if anything just hope the Logitech Webcam C160m will work lol.  I'm going on vacation/honeymoon tomorrow.  So me and the wife need a webcam so we can chat with our 1 year.  Thanks for going through all the trouble.

---

### Post by Script Warlock on 2011-03-26
nah thats no problem and for the meantime just leave your built-in webcam who knows someone has a greater solution for this. and of course goodluck to your vacation hope you enjoy the honeymoon with your new webcam err wife? harharhar...

---

### Post by gokulsurendiran on 2011-07-03
[QUOTE=maddbaron;10598120]if your using gstreamer


 type ```
gstreamer-properties
```  in terminal and go to video, see if your webcam is selected in default input.  The driver should also be video for linux 2... then run test from default input if nothing go to default output and try x window system (no xv) 
 

tried till this, the test result was......
[COLOR="Red"]
*Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.*[/COLOR]

I'm using Samsung N150, didn't have a problem till I was using 10.10, after updating to 11.04.....my web cam is not working.

Any solutions to solve this?

---

### Post by no2498 on 2011-07-04
in gstreamer-properties
try setting the plugin to auto find your cam
use the bottom test button

is also a video 4 so v4l2 compat file you may need

---

