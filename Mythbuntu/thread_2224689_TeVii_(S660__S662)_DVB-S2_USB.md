---
title: "TeVii (S660 / S662) DVB-S2 USB"
date: 2014-05-17
forum: Mythbuntu
---

### Post by bullwinkle2 on 2014-05-17
I'm looking for some current information on these devices.

First, does anyone know the difference between the TeVii S660 and the S662?  The [manufacturer's site]("http://www.tevii.com/Products_S660_1.asp") seems to give no clue on what the difference is.

Second, that page says the device is "USB 3.0 Compatible" but in other places including [this page]("http://www.tevii.com/S660_Specification.pdf") it says that the USB interface is "Universal Serial Bus 2.0 Standard".  So which is it, 2.0 or 3.0?

Third, and the main reason I am asking here - how well do these devices work with the Mythbuntu backend?  Is it pretty much a plug-and-play experience, or do you have to install drivers, or what?  Is it easy, difficult, or nearly impossible to get these devices to work correctly? ("Easy" for me would be the equivalent of hooking up a HDHomeRun.  "Nearly Impossible" would be having to compile anything).

I would be wanting to use such a device for Free-To-Air satellite in North America.  And I did find the [older thread]("http://ubuntuforums.org/showthread.php?t=1378994") on these but the last message was posted well over a year ago and it seemed a lot of people were having trouble back then, and anyway that thread is locked now.  I just wondered if the situation has changed since then, or if perhaps someone has discovered the magic formula to get these to work.

Alternately, I'd be open to other suggestions for tuners that will work "out of the box" as input sources for the MythTV backend under Mythbuntu, if any such exist.  I have been told that TBS and Prof models are not good choices because they require compiling software and other Linux-y things I don't really understand.

Thanks for any suggestions or information anyone can offer!

---

### Post by blm-ubunet on 2014-05-17
Have not used TBS or TeVii devices..
I understand the TBS devices to be very good but you have to use their supplied v4l-dvb (media) kernel module.
They seem to have up-to-date kernel support.

The LinuxTV.org site does not mention S662 at all.
S660 has "built-in" support for sometime.
[http://www.linuxtv.org/wiki/index.php/TeVii](http://www.linuxtv.org/wiki/index.php/TeVii)

TeVii also supply a v4l-dvb branch/driver for S662 (2 months ago) but someone reported it did not work.

There is talk of success using this v4l-dvbbranch for S662
[https://bitbucket.org/CrazyCat/s2-liplianin-v39](https://bitbucket.org/CrazyCat/s2-liplianin-v39)

Possibly, only the S660 will work out of the box.

AFAIK Most of these dvb-s2/t2 sticks need to be plugged into USB2 to work.

Building media v4l-dvb is not so bad but you have to rebuild with every kernel update & you needs lots of build tools & dependencies satisfied..

Sorry if most of the above is unhelpful..

---

### Post by bullwinkle2 on 2014-05-17
> **blm-ubunet said:**
> Have not used TBS or TeVii devices..
I understand the TBS devices to be very good but you have to use their supplied v4l-dvb (media) kernel module.
They seem to have up-to-date kernel support.

The LinuxTV.org site does not mention S662 at all.
S660 has "built-in" support for sometime.
[http://www.linuxtv.org/wiki/index.php/TeVii](http://www.linuxtv.org/wiki/index.php/TeVii)

TeVii also supply a v4l-dvb branch/driver for S662 (2 months ago) but someone reported it did not work.

There is talk of success using this v4l-dvbbranch for S662
[https://bitbucket.org/CrazyCat/s2-liplianin-v39](https://bitbucket.org/CrazyCat/s2-liplianin-v39)

Possibly, only the S660 will work out of the box.

AFAIK Most of these dvb-s2/t2 sticks need to be plugged into USB2 to work.

Building media v4l-dvb is not so bad but you have to rebuild with every kernel update & you needs lots of build tools & dependencies satisfied..

Sorry if most of the above is unhelpful..

Actually, that was quite helpful.  I was just thinking about whether I might want to try one of these devices, but after understanding what is involved I think I'd hold off and see if anything simpler to install and use comes along.

---

### Post by blm-ubunet on 2014-05-17
It does sound worse than it actually is..but then if something fails during compiling/linking you're screwed..

The process is not much worse than using nVidia proprietary video driver but that uses dkms to auto-magically handle updates & also the nVidia releases are very robust.

The S660 has mainline support from kernel 3.0.x.
[http://www.linuxtv.org/wiki/index.php/TeVii_S660](http://www.linuxtv.org/wiki/index.php/TeVii_S660)
But can you still buy that model..

---

### Post by blm-ubunet on 2014-05-23
re: your problem channels:

There are a few mpeg2 video samples that do not play correctly with VDPAU.

[http://www.gossamer-threads.com/lists/mythtv/commits/568186?search_string=mpeg2;#568186](http://www.gossamer-threads.com/lists/mythtv/commits/568186?search_string=mpeg2;#568186)

The "ondine" dvd clip is another.
[http://www.gossamer-threads.com/lists/mythtv/users/569286?search_string=ondine;#569286](http://www.gossamer-threads.com/lists/mythtv/users/569286?search_string=ondine;#569286)

As a workaround you could use CPU decode.
Or upgrade to 0.27+fixes ..
AFAIK 0.27.1 point release is[has] land[ed] shortly.
[http://www.mythtv.org/wiki/Release_Notes_-_0.27.1](http://www.mythtv.org/wiki/Release_Notes_-_0.27.1)

---

