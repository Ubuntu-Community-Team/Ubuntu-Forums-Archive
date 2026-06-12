---
title: "Webcam drivers for Praktica DPix 9000"
date: 2010-06-13
forum: Multimedia Software
---

### Post by LaGrunge on 2010-06-13
Hallo,

recently I've got a digital camera [=551&cHash=bbd11599f0"]Praktica DPix 9000]("http://praktica.de/index.php?id=20&L=1&tx_prdigital_pi1[showUid), which can also be used as USB webcam.

The camera's setup menu allows to configure the USB mode to one off

[LIST]
[*]Disk Drive
[*]Webcam
[*]Printer (for printing directly w/o PC)
[/LIST]
When set to disk drive, everything is fine. The USB device is identified as mass storage device and is automounted when preccing the cam's power button.

When configuring the camera as USB webcam, it's not recognized, and I can't get it to work as an video input device.
I tried opening it in cheese and in webcamstudio after loading several modules from kernel/drivers/media/video, but without success.

lsusb output for the webcam device is: 
```
Bus 006 Device 003: ID 084d:000c Minton Optic Industry Co., Inc. 
```(verbose output is attached)

_Edit:_ dmesg output from connect / disconnect the camera as webcam:
```
[ 1958.572479] usb 6-1: new full speed USB device using ohci_hcd and address 3
[ 1958.965540] usb 6-1: configuration #1 chosen from 1 choice
[ 2188.530299] usb 6-1: USB disconnect, address 3
```Using Windows XP (inside VirtualBox) it works after installing drivers from the cdrom supplied with the camera. Windows identifies the camera as "PC Cam", the drivers come from Syntek Ltd. It installs two drivers: 'Syntek UsbCamd Mini Driver' (MSETUPW1.sys) and 'Syntek UsbIntel Mini Driver' (MSETUPW2.sys).

Has anybody experiences with this camera, or eventually other similar cameras (e.g. older models)?

Any suggestions how to get it to work?

Thanks.
LaGrunge


Additional info:

Ubuntu version: Ubuntu 9.10 - Karmic Koala, AMD64
_Edit:_ Kernel: Linux 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 02:41:03 UTC 2010 x86_64 GNU/Linux

---

### Post by no2498 on 2010-06-13
try wxcam 
read and install all the page tells you to also comes in a deb file

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

now lets try to find the cam
turn the cam on to webcam mode

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope this helps

---

### Post by LaGrunge on 2010-06-14
Hello, 

thanks for your reply, but it didn't work. I've tried the following yesterday

[LIST=1]
[*] I upgraded to kernel 2.6.31-22. No change.
[*]I've downloaded wxCam and compiled it for AMD 64. It doesn't recognize the camera.
[*]gstreamer-properties gives error messages. Here is the console output:
[/LIST]
  ```
$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
libv4l2: error getting capabilities: Inappropriate ioctl for device
libv4l2: error getting capabilities: Inappropriate ioctl for device
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
 
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(198): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2:
Device opened, but wrong type (0x0)]

libv4l2: error getting capabilities: Inappropriate ioctl for device
libv4l2: error getting capabilities: Inappropriate ioctl for device
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(98): gst_v4l2_get_capabilities (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src4:
system error: Inappropriate ioctl for device]
$
```Blank lines are added for readibility: first block of mesages is after startup, second block is when testing v4l1, third block is the output with v4l2. Popup messages in the GUI containe the message text from above. 

The error messages from gstreamer-properties are effectively the same as with no camera connected.

Device /dev/video0 is the "Video loopback 0 input" and is created at boot time together with /dev/video1.
No other video device is created in /dev when connecting the camera.

This camera seems to be ignored.

---

### Post by no2498 on 2010-06-15
ok try this program its in synaptic xawtv

it just helped some one else

hope it helps you

retry cheese if it does not come on at first

---

### Post by LaGrunge on 2010-06-15
Hi, 

both programs - xawtv and cheese - don't recognize the camera. 

It doesn't really surprise me: when I attach the camera it's recognized as USB device, but no additional module is loaded, nor does it create a v4l device node in /dev.

I guess, I first need to find a suitable kernel module which can handle the camera. I've tried several from the /lib/modules tree (in fact all of them at once) but this didn't work.

It would probably help to know if somebody found a working module for an earlier DPix model.

---

### Post by no2498 on 2010-06-15
try changing the plugin in gstreamer-properties
click video

---

### Post by LaGrunge on 2010-06-16
Hi,

I've realized, that I've got the vloopback device active (which came with webcamstudio) and thought it might disturb the detection of the camera. So I've deactived the service: 

```
$ sudo update-rc.d -f vloopback remove
$
```Now, after reboot I don't have 'videodev' or 'vloopback' module loaded and no video device in /dev:

```
$ lsmod | grep vloop
$ lsmod | grep video
$ ls -la /dev/vid*
ls: cannot access /dev/vid*: No such file or directory
$
```Now after connecting the camera lsusb lists it as an Minton device:

```
Bus 006 Device 002: ID 084d:000c Minton Optic Industry Co., Inc. 
```Still no module 'videodev' loaded and no video device in /dev:
```
$ lsmod | grep vloop
$ lsmod | grep video
$ ls -la /dev/vid*
ls: cannot access /dev/vid*: No such file or directory
$
```Last lines from dmesg output:
```
[  379.313801] usb 6-1: new full speed USB device using ohci_hcd and address 2
[  379.686382] usb 6-1: configuration #1 chosen from 1 choice

```xawtv doesn't find a video device:

```
$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.31-22-generic)
xinerama 0: 1680x1050+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
$
```cheese gives message "No camera found!" and displays a test pattern.

I've tried gstreamer-properties again and tried the plugins on the 'Video' tab:

[LIST]
[*] plugin 'Video for Linux (v4l)' gives message "Device "/dev/video0" does not exist".
[*]plugin 'Video for Linux (v4l2)' gives message "Cannot identify device '/dev/video0'".
[*]plugin 'Test Input' works, but display a test pattern, not the camera image (as exepected...)
[/LIST]
  Here is the output:

```
$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src4:
system error: No such file or directory]
$
```Summarized: so far no success with this device.

---

### Post by no2498 on 2010-06-17
try this it may help
put in a terminal 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by LaGrunge on 2010-06-17
> **no2498 said:**
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
Same result as before (says: No camera found)

---

### Post by no2498 on 2010-06-18
need to ask did cheese come up as you put that in

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese 


you can put any name you like not just cheese

---

### Post by no2498 on 2010-06-18
does the cam connect with usb or fire wire

all the programs you have tried are for usb

and if you have a card in it take it out !

btw on my dv cam i have to set it to live

---

### Post by LaGrunge on 2010-06-18
Hi,

I've tried again with Ubuntu - following your suggestion - this time with the SD memory card removed. 
Same result as before: the camera is not recognized.

To make sure, that the hardware (camera, cable, usb-port, etc.) is still working, I've doublecheked again with Windows XP. It's still working.

All the programs I've tried so far are programs using v4l (or v4l2), none of these is restricted to only USB - nevertheless the camera connects via USB - no firewire (nor any other interface available). 
But I'm sure, that the problem is not on application level.

Probably I should point out the following more clearly:

Except from that the camera is listed as an USB device (see lsusb output), nothing else changes. 
Most notably there is no additional kernel-module loaded together with the USB event (camera connect), hence there is no v4l (or v4l2) device created. 
-> This is the reason why none of the applications is able to find the camera.

The questions are: 

[LIST]
[*]Is any of the modules from /lib/modules/`uname -r`/kernel/drivers/media/video/ capable of driving this USB device?
[*]Which options to use for the module?
[*]Is there any 3rd-party driver, which can handle the camera?
[/LIST]
 Until now, I wasn't able to find an answer to any of these questions myself. Any help on this is welcome.

---

### Post by LaGrunge on 2010-06-19
Now I found the technical specs for similar cameras from Minton Optic at their homepage:

[http://www.minton.com.tw/english/main.php?Navi=mCate&CateID=31&mCateID=25](http://www.minton.com.tw/english/main.php?Navi=mCate&CateID=31&mCateID=25)

The technical specification matches with model [Brica DigiArt F161S]("http://www.minton.com.tw/english/main.php?Navi=ProductDetails&ProductID=137") / [F162S]("http://www.minton.com.tw/english/main.php?Navi=ProductDetails&ProductID=138") / [F169S]("http://www.minton.com.tw/english/main.php?Navi=ProductDetails&ProductID=140").

The pictures shown in the User's manual for the [=551&cHash=bbd11599f0"]Praktica Dix 9000]("http://praktica.de/index.php?id=20&L=1&tx_prdigital_pi1[showUid) show a camera having the same case as the [Brica F129]("http://www.minton.com.tw/english/main.php?Navi=ProductDetails&ProductID=110") (but without any branding). The case of the real Praktica DPix 9000 is only slightly different.

If somebody has managed to get a Minton Brica model to work with Ubuntu (or other Distro), details on this might help.

---

### Post by no2498 on 2010-06-20
you must be missing a v4l lib
see if you have v4l-10 plugins
and v4l2-10 plugins

v4l in synaptic

---

### Post by LaGrunge on 2010-06-20
nope. v4l is alright.

The problem is, that there is no kernel module which is creating the /dev/video* character device.

---

### Post by no2498 on 2010-06-20
The gpsca video for linux (v4l) driver, provides support for
webcams and digital cameras based on the spca5xx range of chips
manufactured by SunPlus, Sonix, Z-star, Vimicro, Conexant, Etoms,
Mars-semi, Pixart and Transvision.

The gspca driver is a rewrite of the well known spca5xx v4l kernel
module from the same author, Michel Xhaard.


is this the 1 you need its in the v4l also

---

### Post by no2498 on 2010-06-21
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

see if that helps

---

### Post by LaGrunge on 2010-06-21
Hi, 

thanks your attempt to help. I might go back to the HOWTO once I got the issue with the kernel module solved in case of errors or problems with application programs or libraries.

After digging into the problem over the last weekend, I can conclude the following:

This camera is not supported by kernel 2.6.31 as shipped with Ubuntu. 
As far is I found out by testing and by checking the kernel sources, none of the modules recognizes USB ID 084d:000c out of the box.

I've also traced the USB data stream on a Windows system (using [usbsnoop]("http://benoit.papillault.free.fr/usbsnoop/")) and checked the output against the kernel sources, with an interesting result:

The initialization sequence I found in the trace file is very very close to what is done in the gspca_stk014 module! 

The module itself doesn't work directly with the DPix 9000, because there are some differences, but it might work after some changes. I've tried already at the weekend, and got it running until the first video frame was returned from the camera - then it got stuck... 

If I find the time, I'll probably continue with this. I will post here, if make some progress.

---

### Post by LaGrunge on 2010-06-22
Success! First video stream received about an hour ago!

I've been using a hacked version of gspca_stk014.ko, modified to work with the Praktica DPix 9000 rather than Syntek DV4000. Changes are moderate.
Unfortunetly I also had to modify gspca_main.ko - need to see if this is really required.

---

### Post by no2498 on 2010-06-23
glad you got it working
now tell every 1 how you did it
then edit your first post to say solved 

[solved] Webcam drivers for Praktica DPix 9000

---

