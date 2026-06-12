---
title: "My Logitech webcam used to work in 8.10 and it doesn't in 9.04! Help!"
date: 2009-05-16
forum: Multimedia Software
---

### Post by the8thstar on 2009-05-16
My webcam used to work in Ubuntu 8.10 and now it's not in 9.04! What could I do?

Here is my *lsusb*:

> the8thstar@the8thstar-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by the8thstar on 2009-05-17
BUMP, thank you.

---

### Post by miguelmiranda on 2009-05-27
I have the same problem
Here is my *lsusb*:
Bus 001 Device 006: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 002: ID 046d:08c1 Logitech, Inc. QuickCam Fusion
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0421:0070 Nokia Mobile Phones 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 002: ID 04a5:7008 Acer Peripherals Inc. (now BenQ Corp.) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

any help would be apreciated.

---

### Post by loell on 2009-05-27
> **the8thstar said:**
> BUMP, thank you.

hi, i couldn't offer a solution, but i'm quite intrigued by this particular webcam regression.

what's the error when using webcam apps?

---

### Post by FarNorthRod on 2009-05-27
First post and new ubuntu and linux user so apologies if I've missed something obvious. I installed 9.04 so don't know about the webcam working in previuos versions.

I have a Logitech Quickcam Connect and it too doesn't work.

My lsusb:
Bus 001 Device 002: ID 03f0:6b11 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I run Cheese all seems well at first, the camera's little green light comes on to show it's working then Cheese abruptly closes with no explanation.

gstreamer-properties has exactly the same effect after pressing test.

In Skype after pressing test on the video options screen nothing happens but at least skype doesn't quit.

---

### Post by kavurt on 2009-05-27
> **loell said:**
> hi, i couldn't offer a solution, but i'm quite intrigued by this particular webcam regression.

what's the error when using webcam apps?

I have the same situation with my webcam. My lsusb gives this:
Bus 003 Device 002: ID 046d:08ae Logitech, Inc. Quickcam for Notebooks

But when I try skype, it can't find any webcams.

When I first installed 9.04, skype used to find a webcam, but it showed only a black screen. So I tried the following solution, which worked on 8.04 and 8.10.

[http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html](http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html)

According to that solution, I used to add "blacklist zc0301" to the /etc/modprobe.d/blacklist file. But in 9.04, there's no blacklist file. So I added the same line into the blacklist.conf file. But after that, skype couldn't find any cams. 

I almost gave up. And I continue with 8.04 for now.

---

### Post by loell on 2009-05-27
try the common solution for skype webcam problems that exist in 8.10 and 9.04 .

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
```

---

### Post by jimbo99 on 2009-05-27
> **loell said:**
> try the common solution for skype webcam problems that exist in 8.10 and 9.04 .

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
```

Only he didn't tell you how to do it, nor where to put that.

---

### Post by loell on 2009-05-28
> **jimbo99 said:**
> Only he didn't tell you how to do it, nor where to put that.

those who are asking in this thread are quite aware of the terminal, try analyzing the posts,  so let's not dumb it down.

---

### Post by miguelmiranda on 2009-05-28
The mic works perfect, but the webcam that used to be in dev/video0 does not exist, Cheese says there is no webcam instaled.

I try the common solution for skype webcam problems that exist in 8.10 and 9.04 and that is what i get:
 bt_audio_service_open: connect() failed: Conexión rechazada (111)

Skype works, but no video device is found.

---

### Post by miguelmiranda on 2009-05-29
In order to aport more information i found a grafic device display, and that it:

USB Device 0x46d:0x8c1 Sound Card

instead of the lsusb

Bus 001 Device 002: ID 046d:08c1 Logitech, Inc. QuickCam Fusion
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0421:0070 Nokia Mobile Phones 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04a5:7008 Acer Peripherals Inc. (now BenQ Corp.) 
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Any ideas?

---

### Post by LucaBri on 2009-05-29
> **loell said:**
> those who are asking in this thread are quite aware of the terminal, try analyzing the posts,  so let's not dumb it down.

That's what I call a dumb answer!

It must be tough for those born with embedded knowledge to tolerate those pests who are trying to learn from scratch.

Anyways, I have a similar problem and the common solution does not work for me.

Luca

---

### Post by loell on 2009-05-29
> **LucaBri said:**
> That's what I call a dumb answer!

so be it then, i won't argue. it remains the same.

> **LucaBri said:**
> 
It must be tough for those born with embedded knowledge to tolerate those pests who are trying to learn from scratch. 

if you view yourself or new users as pest? it's up to you. I don't share that opinion.


> **LucaBri said:**
> 
Anyways, I have a similar problem and the common solution does not work for me.

Luca

keep on searching, probably ask nicely? have patience.

---

### Post by loell on 2009-05-29
> **miguelmiranda said:**
> In order to aport more information i found a grafic device display, and that it:

USB Device 0x46d:0x8c1 Sound Card

instead of the lsusb

Bus 001 Device 002: ID 046d:08c1 Logitech, Inc. QuickCam Fusion



Any ideas?

hi, does this webcam used to work in 8.10?

**--edit**

according to [UVC website]("http://linux-uvc.berlios.de/") this webcam has been problematic, it suggest to use another webcam model that is more compatible with the uvc driver, the more compatible lists are also available in their site.

---

### Post by yomm on 2009-06-01
> **loell said:**
> try the common solution for skype webcam problems that exist in 8.10 and 9.04 .

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
```


loell ,
My cam used to work ootb also in ubuntu 8.* , but only partially in jaunty. Cheese seems to be the only app able to access the cam by default.other apps like puredata & opencv etc ..do not see my cam ,and sometimes even segfault
After running your line of code , I can launch camorama & other apps (by replacing '/usr/bin/skype' with whatever ) ,but still the image is scrambled.
Any further suggestions ?

lsusb : 

*
Bus 008 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect
*

with kind regards,

yomm

---

### Post by dusauton on 2009-09-21
> **the8thstar said:**
> My webcam used to work in Ubuntu 8.10 and now it's not in 9.04! What could I do?

Here is my *lsusb*:

Hi the8thstar,

I finally managed to solve this issue by adding my user to the 'video' group...
```
sudo adduser <myuser> video
```
After rebooting... there it was! My brand-spanking new Skype was back in shape with its camera feature working!
Makes my mother happy ;-)

Hope it solves the problem for you too.

---

### Post by carniola on 2009-10-10
**dusauton**: You are my hero. Thanks!

---

