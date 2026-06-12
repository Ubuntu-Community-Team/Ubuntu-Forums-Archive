---
title: "please help - Creative Lab Webcam Live Ultra"
date: 2008-04-24
forum: Multimedia Software
---

### Post by tabalchi on 2008-04-24
Hi All,

For the last week or so I have searched & tried almost everything to setup/configure my Creative Lab Webcam Live Ultra (as seen on [http://193.95.171.84/wwimages/video/Live-ultra.jpg](http://193.95.171.84/wwimages/video/Live-ultra.jpg))  on my new UbuntuStudio - Gutsy 7.10 i386 kernel 2.6.22-14-rt (by the way, I LOVE this OS).

I tried both spca5xx and gspca.  I was not able to install spca5xx at all (make will fail) however, I know gspca is installed and working correctly because I am able to connect my other webcam (Intel cs430) - which works just fine with camorama.  The Creative Webcam Lab Liver Ultra will not work  & camorama cannot find device /dev/video0.  With Creative Lab Webcam Live Ultra plugged-in, here is what dmesg returned:

[61902.988100] usb 2-2: new high speed USB device using ehci_hcd and address 9
[61903.112479] usb 2-2: configuration #1 chosen from 1 choice

I have even reinstalled the entire OS with the cam plugged-in - but had no luck.  I do believe the Creative Lab Webcam Live Ultra 'is' supported - as stated on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html).  However, if you think this is 'not' supported I will go ahead and get another webcam for this server instead.

I appreciate any and all the help I can get on this. 

Many Thanks,
Tabalchi

---

### Post by linuxwizard on 2008-04-24
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga didn't work post results of the command > lsusb

---

### Post by tabalchi on 2008-04-25
Sorry, unable to detect the device with Ekiga; I tried both 'V4L' and 'V4L2' - had no luck.  Here is the output from lsusb:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:7504 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 009: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra
Bus 002 Device 003: ID 03f0:0f07 Hewlett-Packard 
Bus 002 Device 004: ID 0d49:7212 Maxtor 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I really appreciate your help.

---

### Post by linuxwizard on 2008-04-25
According to this (your cam is listed) > [http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx)

Your cam might work with this driver > [http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html)

---

### Post by tabalchi on 2008-04-25
Wow!!! I was able to build and load the drivers and now camorama & Ekiga both work (but I have to start camorama with command line 'camorama -d /dev/video0').  However, I am unable to adjust the image (Brightness, Contrast, ...) with Ekiga or Camorama.  Is there any other way to adjust the pic quality?

Many Thanks,
Tabalachi

---

### Post by linuxwizard on 2008-04-25
Open Camorama > In the white box under effects > right click > add filter > color correction.

When you have Ekiga open along the bottom there is a video tab click on it, their you can adjust color, brightness.

---

### Post by tabalchi on 2008-04-25
In both camorama and Ekiga the Buttons for Contrast and Brightness ... will move but has no affect on the picture quality.  Camorama filters are working though but I am still unable to turn it brighter with either one. Many Thanks

---

### Post by linuxwizard on 2008-04-25
The only thing I can think of is the driver quality. It is classified might work & untested for your cam. That maybe the best picture you will get.

---

### Post by tabalchi on 2008-04-25
I am certainly better off now, at least I am getting a pic.  So I really appreciate all your help - I will keep an eye to see if they will have a new    rev of this driver.

Many Thanks
tabalchi

---

### Post by linuxwizard on 2008-04-25
Yes glad to hear that your webcam is working for you now. And I would keep an eye on a update for that driver. Also glad that I was able to help you. Good Luck

---

### Post by guillo on 2008-05-23
Sorry if this sounds like a stupid question, but how do you install the driver?
I extracted the following files:
camera.h
clultra.c
clultrainit.c
clultrainit.h
clultra.o
Makefile

Thanks for your help!

---

### Post by VHans on 2008-05-26
> **tabalchi said:**
> Wow!!! I was able to build and load the drivers and now camorama & Ekiga both work (but I have to start camorama with command line 'camorama -d /dev/video0').  However, I am unable to adjust the image (Brightness, Contrast, ...) with Ekiga or Camorama.  Is there any other way to adjust the pic quality?

Many Thanks,
Tabalachi

How did you make this work?

---

### Post by ashwinipn on 2008-08-13
> **tabalchi said:**
> Wow!!! I was able to build and load the drivers and now camorama & Ekiga both work (but I have to start camorama with command line 'camorama -d /dev/video0').  However, I am unable to adjust the image (Brightness, Contrast, ...) with Ekiga or Camorama.  Is there any other way to adjust the pic quality?

Many Thanks,
Tabalachi

Hi,
Can you please share the information how you got your webcam work? I visited the website but the information written there is all Greek?latin for me.... I could not find any instruction how to do it... I will be be grateful if you tell you to install the driver..
Thank you in advance...

---

### Post by Raiser on 2010-01-24
> **tabalchi said:**
> Wow!!! I was able to build and load the drivers and now camorama & Ekiga both work (but I have to start camorama with command line 'camorama -d /dev/video0').  However, I am unable to adjust the image (Brightness, Contrast, ...) with Ekiga or Camorama.  Is there any other way to adjust the pic quality?

Many Thanks,
Tabalachi

Hello,

I have the same webcam (041e:403c) and managed to make the device recognized by using this driver (sq930x). My dmesg output is as below:

```
[ 4337.031543] sq930-1: sq930_control_dma: read 001f/0000 8
[ 4337.032252] sq930-1: Product: USB 2.0 PC camera 
[ 4337.032256] sq930-1: Device model: Creative WebCam Live! Ultra
[ 4337.032259] sq930-1: Chip: 930b FW: 12
[ 4337.032263] sq930-1: sq930_control_dma: write 3101/00f0 0
[ 4337.049678] sq930-1: Sensor: Sharp LZ24BP CCD
[ 4337.049690] sq930-1: sq930_control_dma: write 5401/0003 21
[ 4337.057678] sq930-1: sq930_control_dma: write 0305/fd00 0
[ 4337.061676] sq930-1: sq930_control_dma: write 0105/ff00 0
[ 4337.117651] sq930-1: sq930_control_dma: write 0105/fc00 0
[ 4337.129650] sq930-1: sq930_control_dma: write 0105/fe00 0
[ 4337.141633] sq930-1: sq930_control_dma: write 0105/ff00 0
[ 4337.153641] sq930-1: sq930_control_dma: write 0105/fb00 0
[ 4337.257608] sq930-1: registered as video0
```Then I tried a program called motion and the led on the cam is on. But the frame it captured is a blank screen. Also I tried the camorama and the output is like this:

```
VIDIOCGCAP
device name = sq930 USB Camera #2
device type = 1
can use mmap()
# of channels = 1
# of audio devices = 0
max width = 640
max height = 480
min width = 48
min height = 32

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGWIN
x = 0
y = 0
width = 320
height = 240
chromakey = 0
flags = 0

VIDIOCGPICT:
bright = 0
hue = 0
colour = 0
contrast = 0
whiteness = 0
colour depth = 24

VIDIOCGMBUF
mb.size = 2097152
mb.frames = 2
mb.offset = 1048576
Unable to capture image (VIDIOCMCAPTURE).
```How did you managed to make this webcam work with camorama? Am I doing something wrong?

Thanks.

(I have another post about making this cam work here: [http://ubuntuforums.org/showthread.php?p=8717167#post8717167](http://ubuntuforums.org/showthread.php?p=8717167#post8717167))

---

### Post by Aximilli on 2011-01-08
I don't suppose you could explain how exactly you built and loaded those drivers, could you?

---

### Post by epud on 2011-01-29
I would really like to know this too. Could somebody post an easy step by stem install guide for users in the future who want to get the webcam working?

---

### Post by friend4u on 2011-03-15
Hi,
  Let me know how to build and load the drivers. I am not that much aware of this linux world.
Thanks

---

