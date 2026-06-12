---
title: "HOWTO: HP laptop webcam"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by potterzot on 2006-10-19
This is using Edgy Etch, don't know how it works with previous versions.  If you have a new HP laptop of the dv2000 series or similar, you probably realized that your webcam doesn't work.  The spca5xx driver documented elsewhere seems like it would support it, but at the time of writing, only the UVL driver supports this webcam.  First, check out this webpage:

To get the UVC driver, go to:

```
http://linux-uvc.berlios.de/
```

you probably have to install svn:

```
sudo aptitude install subversion
```

then check out the source of the UVC driver and compile and install:

```

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
sudo make
sudo make install

```

Thats it!  Ekiga detects my webcam after this with no problem.  Don't know if this fixes the mic, haven't tested it.  At this point it probably doesn't.

My webcam is a Sonix Microdia webcam, with address 0c45 62c0.  You can find this information by doing:

```
sudo lsusb -v
```

and checking through the listings.  You should see a usb 2.0 webcam listing  there somewhere.

---

### Post by Rul on 2006-10-21
Hi,

I did what you said but when I write

sudo make

the terminal answer:

Building USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-27-386/build: No such file or directorymake: *** [uvcvideo] Error 1

I check it out and effectively there si no build file

What can I do?

by the way, the mic is already working...

---

### Post by eitan on 2006-10-26
thanks for posting this howto.
i checked out and installed linux-uvc from svn (trunk) as you suggested.  lsusb does indeed show a sonix webcam.  however, the ekiga wizard still behaves the same way, claiming it did not detect anything.  most annoying.

also, no change to the status of getting my mic to work.

disappointed..

---

### Post by eitan on 2006-10-26
forgot to mention my specs in the previous post:  i'm running an hp dv2000 laptop (core duo).

---

### Post by Bastanteroma on 2006-10-29
When I try to make I get the following message:

/horriss@horriss:~/trunk$ sudo make
Building USB Video Class driver...
cd: 1: can't cd to /lib/modules/2.6.17-10-386/build
make: *** [uvcvideo] Error 2

Do I need to install something to compile things?

---

### Post by anaconda on 2006-10-29
Thank you for the instructions! worked perfectly!

And for you "Bastanteroma"
You need to have kernel headers installed before running the sudo make and sudo make install..

To install kernel headers for your kernel version type: 
sudo apt-get install linux-headers-`uname -r`

EDIT: and ofcourse you also need the compiler...
sudo apt-get install build-essential

PS. I would guess that the webcam stops working each time after installing new kernel.. we just need to install kernel headers for each kernel, and run the sudo make && sudo make install agin..

---

### Post by dimkal on 2006-11-29
webcam now works great on dv2000z (AMDx64), but mic isn't working :(... any ideas?

---

### Post by yostral on 2006-12-07
Mic is working ok with alsa 1.0.13.

---

### Post by anaconda on 2006-12-09
Where/how can I get alsa 1.0.13 ??

I see that the repositories have version 1.0.11
(edgy AMD64)

---

### Post by megamax on 2006-12-15
> **yostral said:**
> Mic is working ok with alsa 1.0.13.

Hi,
i have a hp dv2008ea (AMD TL50x2) but mic don't work...
lspci say 00:10.1 "Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)" and it work with module snd_hda_intel (with options snd-hda-intel model=hp position_fix=1 enable=yes), but mics (external and internal) don't work.. i compiled alsa 1.0.14rc1 (if you're interested  this version automatically switch to headset when you plug it ;) ) but nothing :(
Have you the same chip? Can someone help me? Thanks!

---

### Post by uggeli on 2007-02-13
> **anaconda said:**
> 
PS. I would guess that the webcam stops working each time after installing new kernel.. we just need to install kernel headers for each kernel, and run the sudo make && sudo make install agin..

You were right about that. Now when I got 2.6.17-11-generic kernel webcam stopped working. I tried to install driver again, but nothing happens. Ekiga still claims it doesn't recognize any device. Well there wasn't much use of that cam anyway (maybe it will when gaim will have video support), but sure it would be nice to get it working again.

---

### Post by ZERO_SHIFT on 2007-04-22
I have hp dv2000 followed instr. but Webcam did not work??

---

### Post by uggeli on 2007-06-09
How to get this cam working again? I have upgraded to Feisty for some time ago (I did distupgrade, not clean install) and I'm not able to get this working.

I read at [http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/](http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/) in comments, that someone said at June 5th, 2007 the following:

> 
 Just wanted to mention that using Ubuntu 7.04 the web cam was automatically recognized and Ekiga is able to use it out of the box.


Is this really true, and if so, how to remove drivers (installed like in this how to) proberly, and let ubuntu recognize webcam?

If ubuntu isn't able to recognize webcam, can I try install older revision of driver, or do I have to uninstall old ones first proberly? Just curious cause in that blog there was mentioned that revision 62 worked and you could get it with command: 

 svn checkout -r 62 [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)

BTW. I got error like this for nowdays.

```

$ sudo modprobe uvcvideoPassword:
FATAL: Error inserting uvcvideo (/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

PS. Sorry for my bad English

---

### Post by nuvolavinz on 2007-06-10
hi there, 
ive tried really anything you explained so well,
but still the webcam and the mic are not working.
is there any other thing or driver i should install?
thank you
vinz

ot: cant update covers on ipod using amarok, but thats a long long story... :o

---

### Post by buntunub on 2007-07-20
I am having the same issue as ugglei with the same modprobe error. hp dv2415 here - Sonix Microdia 0c45:62c0. Considering the fact that only a small handfull of folks have actually gotten this thing to consistently work, I guess this webcam is a nogo in Linux right now. :mad:

---

### Post by buntunub on 2007-07-30
Update: Webcam works with fresh Fiesty install in Ekiga. It works with luvcview fine as well. However, luvcview record options seems to be broken (luvcview -f yuvy -S, for example, which you can only playback with a complex mplayer script, only records video, no audio). Using ffmpeg, you can record with both audio and video just great in a .avi format, however, you wont get any playback image while recording, just the bluelight will come on letting you know that the webcam is active. The playback file works great though, aside from a ton of weird audio feedback, which can be mitigated by playing around in alsaconf.

---

### Post by asatishc on 2007-08-02
For those of you who have problems with webcam:
Install uvc drivers as mentioned in one of the previous posts and u can also follow [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)
In Ekiga, select the v4l2 option. After setting up, ekiga does recognize the webcam and it works fine.
Now the problem I faced is the webcam works ONLY with ekiga and nothing else. I tried camorama and xawtv. Camorama gives an error saying 'device not found /dev/video0'. when I open xawtv, the webcam light flashes and it also gives an error. when i exit xawtv, the webcame light flashes again.
Does anyone know how to use the builtin webcam to record the video???
---------------------------
For those of u who have problems with headphones/mic:
Go to alsa website, download alsa drivers, utils, firmware and lib (all version 1.0.14)
install them(use snd card=intel while installing drivers)
and then make a restart. that solves the problem of headphones and mic

---

### Post by asatishc on 2007-08-02
For more details about headphones and mic problem, follow this thread:
[http://ubuntuforums.org/showthread.php?t=455147&highlight=alsa+headphones+mic](http://ubuntuforums.org/showthread.php?t=455147&highlight=alsa+headphones+mic)

I checked the mic with audacity. It worked but with some noise.

---

### Post by 78charlesdarwin on 2007-10-29
wow, that howto worked like a charm. I started out with:
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

FYI for the other laptop owners out there - the microphone is attached to the nvidia hd / Conexant sound card. I found that only the OSS drivers were working for this card (CX20549). ALSA was not working for me in ubuntu 7.10. audio preferances can be changed in System-> Preferences->Sound.

---

### Post by mrpurple on 2007-11-03
hi i tryed different installation but no one work to me . 
my webcam is 0x0c45 0x624f microdia,  under ubuntu 7.10 gutsy gibbon. 
i don't know if i did some mistake in installation or maybe i have to clean other installation that i tryed. 
if some of you have an idea please help me.

---

### Post by noisebeard on 2007-11-21
Sweet.  That worked great.

I installed Cheese and it worked perfectly.

---

### Post by biodiesel-bri on 2007-11-24
On my HP dv9610us the built-in HP webcam was detected out of the box (064e:a110).  I wasted a lot of time trying to get it to work but all I had to do was change Ekiga to V4L2 and it worked like a charm.  Camorama does not work, I guess it only supports V4L.  Cheese works with no modifications.

---

### Post by scorp123 on 2007-11-27
Bump!

I have a HP **dv2108ea** and the web cam is a "Microdia" (0c45:62c0) ... so it *should* work, right? But it doesn't :(

_uvc module:_
I got the newest from the SVN repositories (as of this writing: Revision 147) and the module compiles and loads just fine. The option "trace=15" produces lots of output.

_luvcview:_
Compiles OK. When I try to run this line of code:
```
luvcview -d /dev/video0 -f yuv -s 320x240
``` ... I get error messages the first 2-3 times, it will eventually run if I keep trying. Using higher resolutions e.g. 640x480 gives me a completely green camera image.

_Ekiga:_
Camera is detected but only gives me completely green image. But other than that I can turn on / turn off the camera.

_xawtv:_
Camera gets turned on for a brief moment (no picture though; the window remains completely black) but after that I get error messages about "capture failed".

_Skype 2.0 beta:_
Camera gets detected, but "Test video" only gives me completely black window.

Given these symptoms I would assume I have a hardware or firmware problem somehow? As I said ... the "uvcvideo" drivers do load OK and "luvcview" will produce an image if I don't put the resolution too high (e.g. anything beyond 320x240 will produce a completely green camera image)

I would appreciate to hear from those who got the same camera and got their's to work ....

---

### Post by gothicsoul on 2007-12-04
Hi there, 

I've the 0c45:627b, on the 7.10 64bit AMD, eveything installed OK but the webcam is not detected, there is no /dev/video0.

Any idea ?

Thx! :-)

```
Bus 002 Device 007: ID 0c45:627b Microdia 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0c45 Microdia
  idProduct          0x627b 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 USB20 Camera    
  iSerial                 0 
  bNumConfigurations      1

```

---

### Post by joh6nn on 2007-12-09
luvcview worked perfectly for me using the debian package, available here: [http://packages.debian.org/testing/x11/luvcview](http://packages.debian.org/testing/x11/luvcview).  i haven't tried any other packages yet, but there's a good possibility that some apps just aren't written to use this type of camera

---

### Post by Leo the Lion on 2008-01-14
> **potterzot said:**
> This is using Edgy Etch, don't know how it works with previous versions.  If you have a new HP laptop of the dv2000 series or similar, you probably realized that your webcam doesn't work.  The spca5xx driver documented elsewhere seems like it would support it, but at the time of writing, only the UVL driver supports this webcam.  First, check out this webpage:

To get the UVC driver, go to:

```
http://linux-uvc.berlios.de/
```

you probably have to install svn:

```
sudo aptitude install subversion
```

then check out the source of the UVC driver and compile and install:

```

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
sudo make
sudo make install

```

Thats it!  Ekiga detects my webcam after this with no problem.  Don't know if this fixes the mic, haven't tested it.  At this point it probably doesn't.

My webcam is a Sonix Microdia webcam, with address 0c45 62c0.  You can find this information by doing:

```
sudo lsusb -v
```

and checking through the listings.  You should see a usb 2.0 webcam listing  there somewhere.

Hi Potterzot!
Before I did any of the above to get my webcam working in Ekiga, I did the following:
Edit>Preferences>Devices>Video Devices
In "Video Plugin" select V4L2.
This got my webcam working, but only in Ekiga. Now I'm trying to get it working in GIMP, but haven't had any luck yet. Does anybody have any ideas on how to enable the webcam on GIMP?

---

### Post by vivalant on 2008-01-14
> **gothicsoul said:**
> Hi there, 

I've the 0c45:627b, on the 7.10 64bit AMD, eveything installed OK but the webcam is not detected, there is no /dev/video0.

Any idea ?

Thx! :-)

```
Bus 002 Device 007: ID 0c45:627b Microdia 


```


Try the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by mc-rpg on 2008-04-06
Wow, thanks dude. Everything worked like a charm here, even the mic worked. Mine is an HP Pavilion dv2423la. From what I've heard this webcams used to work under ubuntu before, hope they work again on Hardy, I haven't had the chance to try the Betas to check it out. I tested it with aMSN (Not that I use it but was the only way to test it I knew before knowing Cheese) and Cheese.

---

### Post by janaha on 2008-04-27
Sweet.Worked great on my HP dv6185eu (0c45:62c0 Microdia)
Thanks alot!

---

