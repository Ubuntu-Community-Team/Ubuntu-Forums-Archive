---
title: "How do I install video driver?"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by blackdalek on 2006-08-07
I am a new linux user. I have installed ubuntu today on a box I cobbled together from very old bits and pieces lying around the shed.
The video card in it is an S3 Virge/DX - this doesn't seem to be working properly. The device manager thingy in system aministration says it's an S3 Virge DX/GX, but it doesn't list anything for the card's capabilities (just says "unknown").
The display resolution changer control panel thingy is only listing 640x480 and 800x600 - I'm pretty sure this card supported higher resolutions than that, if I remember correctly. Not sure if this is a 2Mb or 4Mb card.
I was able to find this page through searching [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxserver-xorg-driver-s3virge_6.8.2-77.1_i386.deb&md5sum=94c2e1301d67d768de61870d2a642a23&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fx%2Fxorg%2Fxserver-xorg-driver-s3virge_6.8.2-77.1_i386.deb&md5sum=94c2e1301d67d768de61870d2a642a23&arch=i386&type=security)
which I believe may be a video driver for S3 Virge cards, but I am at a loss as to what to do with this file once I've downloaded it.
I've been searching for beginners instructions on how to install drivers into linux, but so far have not turned up anything useful.
I have only had experience with installing drivers in DOS and Windows.

---

### Post by croak77 on 2006-08-07
Check to see if this is installed;

xserver-xorg-driver-s3virge

If not you should be able to install it.Open a terminal and enter; 

```
sudo aptitude install xserver-xorg-driver-s3virge
```

After installing you might have to reconfigure X. From a terminal enter;

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you some questions about your display driver, resolution, etc.

---

### Post by blackdalek on 2006-08-07
Please bear with me... I have no internet or LAN connection on my linux machine, so I am copying files across to the linux computer on 3.5 floppies. I worked out that the .deb file I can double click and it starts to install - then it gives me an error saying that I already have a more up-to-date version of this driver installed.

> **croak77 said:**
> Check to see if this is installed;

xserver-xorg-driver-s3virge

If not you should be able to install it.Open a terminal and enter; 

```
sudo aptitude install xserver-xorg-driver-s3virge
```

After installing you might have to reconfigure X. From a terminal enter;

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you some questions about your display driver, resolution, etc.

I will try out some of those commands in the terminal and see what they do.

---

### Post by blackdalek on 2006-08-07
ok, I ran the configuration thing (sudo dpkg-reconfigure xserver-xorg) in a terminal window - answered all the questions about video and entered 4096 into the question about how much video ram... after that was finished nothing seemed to change - still only 800x and 640x in the display resolution and still no more/different info in the device manager so I restarted the machine to see what happens and still no change.
What do I try next?

---

### Post by blackdalek on 2006-08-07
ok. I'm lost.
Am I missing a step or something?
What exactly does running "sudo dpkg-reconfigure xserver-xorg" in a terminal window do?
Because as far as I can tell it ain't doing nothing. I answer a bunch of questions about video, mouse and keyboard, but the end result is nothing happens or changes.
I don't understand what is meant to be happening or how this might help with the problem of the s3 Virge DX card not working properly.

Should I just conclude that this card simply isn't supported and look for a different card off eBay?

---

### Post by croak77 on 2006-08-07
There is a resolution option when you do sudo dpkg-reconfigure-xserver-xorg. You might have to select 'expert' when it asks you about your monitor. Then you can select resolutio, Vertical/Horizontal frequency.

But bying a new card might not be a bad idea.

---

### Post by tseliot on 2006-08-07
> **blackdalek said:**
> ok. I'm lost.
Am I missing a step or something?
What exactly does running "sudo dpkg-reconfigure xserver-xorg" in a terminal window do?
Because as far as I can tell it ain't doing nothing. I answer a bunch of questions about video, mouse and keyboard, but the end result is nothing happens or changes.

After you answer all those questions you need to restart the Xserver.

In other words:
log out and press CTRL+ALT+Backspace

---

### Post by blackdalek on 2006-08-07
> **tseliot said:**
> After you answer all those questions you need to restart the Xserver.

In other words:
log out and press CTRL+ALT+Backspace

Thank you, I tried those other steps you suggest to restart Xserver, and now something has actually changed. I still get only 800x600 and 640x480, but now instead of a choice of 60Hz or 50Hz I only get one choice fixed at 73Hz.

When I went through "sudo dpkg-reconfigure xserver-xorg" I first tried the advanced option for monitor setup, but then realised I didn't know enough about or even understand what horizontal and vertical sync ranges were all about, so I started again with the medium option which just let me tell it maximum resolution possible on the monitor is 1024x768 @75Hz.\

Obviously this hasn't worked for me either.

Anything else I should try?

---

