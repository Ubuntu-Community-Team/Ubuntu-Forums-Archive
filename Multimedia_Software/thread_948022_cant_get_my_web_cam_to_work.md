---
title: "cant get my web cam to work"
date: 2008-10-14
forum: Multimedia Software
---

### Post by cowboyup8606 on 2008-10-14
i plugged in my web cam and i cant get it to work and i dont know why when i used to have windows xp and had ubuntu runnin under it my cam worked on ubuntu when i had the cam installed on xp ... i dont know why its not workin now can anyone hlp

---

### Post by loell on 2008-10-14
you need to post some more info, while your webcam is plugged 

type

```
lsusb
``` in the command line prompt

copy and past it here.

---

### Post by cowboyup8606 on 2008-10-14
what do u mean post more info ?? like what ??

---

### Post by virtuoso88 on 2008-10-14
I can't get my webcam to work either.  Instead of posting a new topic I figure I'd try and get help here.  

It works with xawtv but freezes eventually.  It use to work with cheese but stopped working and only freezes cheese, and camorama says it can't connect to /dev/video0.  /dev/video0 is there and my username is part of the video group.

Thinkpad W500 with Ubuntu 8.10

v4l-info

> 
### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "UVC Camera (17ef:4807)"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 1280
	maxheight               : 1024
	minwidth                : 48
	minheight               : 32



lsusb

> Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 17ef:4807 Lenovo 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a5c:2145 Broadcom Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsmod | grep video

> uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
video                  25104  0 
output                 11008  1 video
usbcore               148848  5 uvcvideo,btusb,ehci_hcd,uhci_hcd

---

### Post by loell on 2008-10-14
atm, cheese is having trouble getting video from UVC based webcams.

---

### Post by virtuoso88 on 2008-10-14
> **loell said:**
> atm, cheese is having trouble getting video from UVC based webcams.

Should I consider compiling an older build then?

---

### Post by cowboyup8606 on 2008-10-14
is there a type of web cam that supposed linux ?

---

### Post by patrickballeux on 2008-10-14
> **virtuoso88 said:**
> Should I consider compiling an older build then?

I tried reverting to an older version of Cheese and never was able to make it work properly.  

One of the solutions I found was to use the Flashcam project which take your V4L2 device and create a virtual V4L device that you can now use in Camorama/Camstream...

[http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

If you want to broadcast over the internet (using blogTV or Stickam), you can try WebcamStudio for GNU/Linux which can create a virtual webcam with overlays and special effects:

[http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

Using WebcamStudio and gst-launch, I am able to record sound and video into an OGG file that I can then convert and send to any web service like Youtube.

But sadly, Cheese is kind of broken for now...


Good luck!

---

### Post by loell on 2008-10-14
> **virtuoso88 said:**
> Should I consider compiling an older build then?

older builds hasn't address this either. :(

they'll gonna have to use a newer library in accessing webcams, most of the webcam based applications will have to.

i just noticed you're on 8.10 intrepid? , try preloading libv4l. not sure if it will make any difference, but worth a try.

---

### Post by patrickballeux on 2008-10-14
> **cowboyup8606 said:**
> is there a type of web cam that supposed linux ?

Logitech in general are quite well supported.  But newer webcams are V4L2 type and are not supported by the V4L api (older API).  The problem is that all the softwares mostly support only the V4L api even if the V4L2 is now the offical API to use for a few years...

---

### Post by loell on 2008-10-14
> **cowboyup8606 said:**
> is there a type of web cam that supposed linux ?

its kinda cryptic for new users, but here is the list

[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

---

### Post by virtuoso88 on 2008-10-14
Thanks for the help.  

The reason why I ask about reverting to an older build is it use to work with 8.10 and I figured updating broke it some how.

---

### Post by loell on 2008-10-15
> **virtuoso88 said:**
> Thanks for the help.  

The reason why I ask about reverting to an older build is it use to work with 8.10 and I figured updating broke it some how.

ah! i see :D then preloading libv4l will most probably get it working again.
this is a common webcam issue in intrepid. :)

---

### Post by virtuoso88 on 2008-10-15
> **loell said:**
> ah! i see :D then preloading libv4l will most probably get it working again.
this is a common webcam issue in intrepid. :)

Doesn't work.  

> export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export LD_LIBRARY_PATH=/usr/lib/libv4l

It did change the error message on camorama to "Unable to capture image" from "Could not connect to video device".

---

### Post by cowboyup8606 on 2008-10-15
heres what i get for a error when i try to set up my lagiteck web cam 


invalid command name ".assistant1.bodyf.contentf.left.chans"
    while executing
"$chanswidget list get 0 end"
    (procedure "::AVAssistant::StartPreviewLinux" line 15)
    invoked from within
"::AVAssistant::StartPreviewLinux .assistant1.bodyf.contentf.left.chans ZC301-2"
    ("after" script)

---

