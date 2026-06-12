---
title: "Xbox 360 Live Vision camera in Ubuntu?"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2006-10-24
I realize this is a funny combination, but does anyone know if the Xbox 360 Live Vision camera can be made to work with Ubuntu?  It was designed to be used with an Xbox 360 video game console... and as far as PC use, MS provides only WinXP drivers, and even those require XP Service Pack 2, so I understand this is a long shot.

But if I can save some money and not have to buy a separate webcam for the PC, that would be great!

Thanks for any info you may have.

-Mark

---

### Post by ser1alsn1per on 2006-11-15
Yeah  i have 1 to 

ser1alsn1per is my gamertag battlefeild 


but camera on ubuntu  will be sweet

---

### Post by pek on 2006-11-16
so why don't you plug it in and see what lsusb says?

---

### Post by Otaconda on 2006-11-29
> **pek said:**
> so why don't you plug it in and see what lsusb says?
Allow me:

```
daz@toledo:~$ lsusb
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 046d:c30a Logitech, Inc.
Bus 002 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 07cc:0501 Carry Computer Eng., Co., Ltd
Bus 001 Device 004: ID 045e:0294 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
```
Not the most useful description.  Googling that ID doesnt reveal anything, and I'm far from an expert on these things so not sure where to go next really.

See [here](http://dwuk.net/forum/ubuntu/lsusb_output.txt) for '-a' output.

---

### Post by disc on 2006-12-11
Please update us if you figure out a way to get the camera work.

---

### Post by cenithx on 2007-01-31
Keen to see if anyone has figured this out as well.

On windows it detects as a webcam..

Anyone got any ideas on whether this would be possible on ubuntu?

---

### Post by smiley2billion on 2007-02-08
I'm getting a 360 with a Vision camera soon, so I'll start plugging at this when I get it.  Also, does anyone know a way to stream video to the 360?  I've heard of the VLC method but I think that requires setting up Windows Media Connect in WINE or some such nonsense.  I'd be more interested in something that just allows the 360 to see whatever videos I want to stream/share.

---

### Post by ChaseSechrist on 2007-06-17
I know this is a long bump, but has anyone gotten any further with this?

---

### Post by ChaseSechrist on 2007-06-17
Alright, apparently this camera is a standard UVC camera.

If only there was a way to force it to use the driver X_X.

---

### Post by Dag J. on 2007-07-08
Still no luck? Me sad :(

---

### Post by DavidGX on 2007-07-14
I'd really like to see if this is possible. Bump!

---

### Post by Ralob on 2007-07-20
mine works *shurgs* all I did was plug it in and follow these instructions: [https://help.ubuntu.com/community/Webcam#head-33aa4b4ca9f69aea5932b0ce057bf5bfbf8a932f](https://help.ubuntu.com/community/Webcam#head-33aa4b4ca9f69aea5932b0ce057bf5bfbf8a932f)

---

### Post by mjpatey on 2007-07-21
@Ralob,

Really?  I just followed that to a "T" and still nothing recognizes the Xbox 360 webcam.  I'm running Feisty currently.  I also installed EasyCam, and had no luck there.

It may be time for me to break down and buy one of the webcams listed as compatible with the PWC driver:

[http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC]("http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC")

The QuickCam Orbit can be had for $99 USD from newegg.

Glad this thread is still alive!  I'd like to know what kind of setup Ralob has, etc.  Maybe I need to reinstall the driver or something?

-Mark

---

### Post by karishbhr on 2007-12-07
anyone get this to work at all?

---

### Post by PsyCHZZZ on 2007-12-07
Yeah... another curious person here. I got one lying at home and would love to get it to work. 
Might try and tinker with it over the weekend and see what comes up.

---

### Post by PsyCHZZZ on 2007-12-08
Guess what? I managed to get it working on my Ubuntu server! :D 

[IMG]http://www.benetleong.com/wp-content/xbox_cam.png[/IMG]
[IMG]http://www.benetleong.com/wp-content/xbox_stream.png[/IMG]

I've written a step-by-step guide on how to install it with the latest UVC driver and also testing it using uvc_streamer. 

Here's the link:
[http://benetleong.com/2007/12/08/howto-setup-xbox-360-live-vision-camera-in-ubuntu/](http://benetleong.com/2007/12/08/howto-setup-xbox-360-live-vision-camera-in-ubuntu/)

Please note that I'm running this on Ubuntu 7.10 Server (2.6.22-14-server). I'm not sure if it'll work with older version of kernels but it's worth a shot.

Cheers~

---

### Post by Xanghi on 2007-12-11
Well no we need to get it workning on desktop and im getn no where

---

### Post by PsyCHZZZ on 2007-12-12
This should be pretty much the same on the desktop. Just install the drivers as described in the steps and ensure that the device appears on your /dev.

After that, you do not need to install uvc_streamer to test it if you do not wish to... I believe that aMSN supports V4L2 and you should be able to use that with the webcam via your Ubuntu Desktop.

Where are you getting stucked at anyway?

---

### Post by Xanghi on 2007-12-12
well i cant get on my computer i changed video cards and now when i log on it puts lines all through the screen and i cant c anything so idk wt to do to fix it. so im stuck using my wii

---

### Post by PsyCHZZZ on 2007-12-13
Ahh.. right. Well, probably you can try to re-compile and re-install your video card driver? Perhaps you can post in a new thread about this problem and get some of the pros here to help you out.

---

### Post by Xanghi on 2007-12-24
ok so im stuck right at the end i typed in the ls /dev | grep video and it comes up with "file_one" so yeah idk if I type in ls /dev then grep video or ls /dev | grep video sorry im newish to this still but im learning

---

### Post by PsyCHZZZ on 2007-12-24
It seems like you just listed all the items in /dev. The grep command is meant to filter out all the irrelevant ones and just give you the results for video devices.
So, the command should be in 1 line with the pipe

```
ls /dev | grep video
```

From the list you posted, it seems that video0 is not present. Did you manage to find the device when you run lsusb?

---

### Post by Xanghi on 2007-12-25
yeah that was all there and there is no video0 in the list so IDK wt to do. question does the usb port have to be usb 2.0?

---

### Post by PsyCHZZZ on 2007-12-29
> **Xanghi said:**
> question does the usb port have to be usb 2.0?

Yes... it has to be plugged into a USB 2.0 port for it to work... USB 1.1 just doesn't provide enough power.

---

### Post by Xanghi on 2008-01-01
dang it well i have a usb 2.0 pci card put in my computer but when i plug anything in to it they dont work

---

### Post by JOWIROMA on 2008-01-24
> **PsyCHZZZ said:**
> This should be pretty much the same on the desktop. Just install the drivers as described in the steps and ensure that the device appears on your /dev.

After that, you do not need to install uvc_streamer to test it if you do not wish to... I believe that aMSN supports V4L2 and you should be able to use that with the webcam via your Ubuntu Desktop.

Where are you getting stucked at anyway?

Well, I got it working... the only thing is that sometimes it gives me a format error and it says that v4l2 fail to start... the other thing is that I can not find a way to make it work with amsn, I did the set up in the amsn preferences but when you choose the driver nothing happens.

do you have any idea??????

what would happen if you connect a PLAYSTATION EYE USING THIS METHOD????

---

### Post by tkoopa on 2008-01-27
I finally got my 360 vision cam on 7.10. I had the added difficulty of trying to run it on a machine with a tv-card which required extra work. Here's the full details for those that need some more help

I retrieved information from the following pages to write this guide:

[http://benetleong.com/2007/12/08/howto-setup-xbox-360-live-vision-camera-in-ubuntu/](http://benetleong.com/2007/12/08/howto-setup-xbox-360-live-vision-camera-in-ubuntu/)
[https://help.ubuntu.com/community/UVC?highlight=%28uvc%29#head-2d5ac2793123d75b7406e3c94f91b6e0623e3a61](https://help.ubuntu.com/community/UVC?highlight=%28uvc%29#head-2d5ac2793123d75b7406e3c94f91b6e0623e3a61)
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
[http://mxhaard.free.fr/spca50x/Investigation/uvc/?M=A](http://mxhaard.free.fr/spca50x/Investigation/uvc/?M=A)

Start by compiling uvc driver from svn

```

sudo apt-get install linux-headers-`uname -r`

sudo apt-get install subversion

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

cd trunk/

make

```

edit the makefile
```

gedit Makefile

```
```

INSTALL_MOD_DIR := usb/media

to

INSTALL_MOD_DIR := ubuntu/media/usbvideo

```

install it and load it

```

sudo make install

sudo modprobe uvcvideo

or 

sudo modprobe -r uvcvideo

```

Because there is a tv tuner card in this machine the webcam is not /dev/video0

So to solve we need to  a custom udev rule

Identify the webcam

```

lsusb
Bus 005 Device 006: ID 045e:0294 Microsoft Corp. 
....

```

045e is the vendor ident (idVendor) and 0294 the product ident (idProduct).

We have now to create a new file /etc/udev/rules.d/95-perso.rules with this line :

```

sudo gedit /etc/udev/rules.d/95-perso.rules

```

```

KERNEL=="video*", SYSFS{idVendor}=="045e", SYSFS{idProduct}=="0294", SYMLINK+="webcam"

```

 Identify the tuner card
```

lspci

.....
02:09.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
.....

```

With this code 02:09.0 we could find the vendor and device idents :

```

lspci -n 

....
02:09.0 0480: 1131:7134 (rev 01)
....

```

1131:7134 are the vendor and device
Here is the new line for our file /etc/udev/rules.d/95-perso.rules :

```

sudo gedit /etc/udev/rules.d/95-perso.rules

```

```

KERNEL=="video*", SYSFS{vendor}=="0×1131", SYSFS{device}=="0×7134", SYMLINK+="tvtuner"

```

restart udev

```

sudo /etc/init.d/udev restart

```

Try uvc streamer to test the installation

```

sudo apt-get install build-essential

mkdir uvc_streamer
cd uvc_streamer
wget http://naaa.de/programme/uvc_streamer/uvc_streamer_2007_07_11_20.55.20.tgz
tar xzvf uvc_streamer_2007_07_11_20.55.20.tgz
make clean
make all
sudo cp uvc_stream /usr/local/bin/

```

```

uvc_stream -d /dev/webcam

```
the browse to [http://localhost:8080/](http://localhost:8080/)

---

### Post by PsyCHZZZ on 2008-01-27
> **JOWIROMA said:**
> Well, I got it working... the only thing is that sometimes it gives me a format error and it says that v4l2 fail to start... the other thing is that I can not find a way to make it work with amsn, I did the set up in the amsn preferences but when you choose the driver nothing happens.

do you have any idea??????

what would happen if you connect a PLAYSTATION EYE USING THIS METHOD????

The format error and the fail to start error... is that intermittent or do you notice a pattern before you get those errors? 

Also, my apologies as I do not use this on a Ubuntu Desktop environment. So, I won't be able to test the aMSN setup... have you tried asking on aMSN forum and see if the kind ppl there can figure it out? 

> **JOWIROMA said:**
> 
what would happen if you connect a PLAYSTATION EYE USING THIS METHOD????

It might just blow up... :p Just kidding... I dunno. it might just work as well. So, if you have one why not just try plugging it in and test it out? :)

---

### Post by dems on 2008-02-28
I finnaly managed to get it working, by following tkoopa instructions, but you have to use older uvcvideo version beacause latest from svn does not work.

You must replace svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk by
svn checkout -r 147 svn://svn.berlios.de/linux-uvc/linux-uvc/trunk in order to retreive an older version of the driver and then it works like a charm

---

### Post by TigerDX on 2008-04-06
Just wanted to chime in and let you know that tkoopa's method worked great for me! However, I didn't have to worry about the version of *uvcvideo*, it worked as-is from the latest version.

I've tested it working in Skype.

Kernel 2.6.22-14

Edit: In a call, the video coming from me was very choppy - parts of the video were shifting horizontally like an old VCR! What's more, the image was being transmitted to the other party in this broken state. I haven't been able to find what caused this yet, but I'll let you know if I find anything out.

Video is fine in the "test" found in the Skype options, this problem only occurs in calls.

---

