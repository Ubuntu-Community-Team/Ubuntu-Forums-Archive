---
title: "Live Cam Optia (UVC) on Ubuntu 10.04 Lucid Lynx - Black screen nightmare"
date: 2010-05-25
forum: Multimedia Software
---

### Post by RabidFX on 2010-05-25
[B]tl:dr : I went through a lot a sweat to get my webcam working in skype. A lot of problems came from bad diagnosis and wrong solutions. Here is a quick diagnosis how-to for others.
[/B]
1 - Make sure ubuntu recognize your webcam and the driver is properly loaded.
```
lsusb
```
Will tell you that.

2 - Skype needs Xv to work, X11 won't do.
```
gstreamer-properties
```
Will allow you to see what is possible. Video output should be set to X window System WITH Xv. If the test works only with Xv disabled, then you have a graphic drivers problem - it was the case for me.

Original post / thread follows.

-----------------------------------------------------------------------------

Hello fellow Ubuntu users !

It's been a while since I started to enjoy Ubuntu, and generally could solve all my problems by lurking on this forum or around the intertubes...

Today is my first post, because no amount of searching and tweaking could help me this time :(

Ok, let's get to the point :

I have, as the title imply, a Creative Live! Cam Optia plugged (through USB) on a comp with Ubuntu 10.04 Lucid Lynx. 

Webcam seems properly detected / driver'ed, as "lsusb" suggests :
```

Bus 001 Device 004: ID 041e:4057 Creative Technology, Ltd Live! Cam Optia

```Yet, cheeze, gstreamer-properties or skype all show only a black screen. No amount of v4l1compat or v4l2convert magic seems to do the trick.

Here is the result of "dmesg | grep -i video" :
```

[    0.475719] pci 0000:01:00.0: Boot video device
[   16.604209] Linux video capture interface: v2.00
[   16.725660] uvcvideo: Found UVC 1.00 device Live! Cam Optia (041e:4057)
[   16.794827] usbcore: registered new interface driver uvcvideo
[   16.794832] USB Video Class driver (v0.1.0)
[  388.414451] uvcvideo: UVC non compliance - GET_MIN/MAX(PROBE) incorrectly supported. Enabling workaround.
[  389.120661] uvcvideo: device Live! Cam Optia requested null bandwidth, defaulting to lowest.
[  555.021232] uvcvideo: device Live! Cam Optia requested null bandwidth, defaulting to lowest.

```What am I doing wrong ? Besides, what's that about the Live Cam! Optia not being UVC-compliant ? I read all around the web that it was ?

I'm out of ideas. Anyone ?

Thanks.

[Edit] : Oh, and I forgot - it was working perfectly last week ! I don't think I have messed with anything...

---

### Post by RabidFX on 2010-05-25
Ok, I'm getting a bit further :

It turns out that the webcam works very well - I did not think about testing it with someone else.
So apparently my webcam works like a charm, but I cannot see the feed from it [FONT=Trebuchet MS]in any app[/FONT], or any contact's webcam in Skype.

ffmpeg problem ?
I tried reinstalling several gstreamer packages, to no avail. I'm still puzzled, any advice ?

[Edit]
I followed the How-to in this forum, in order to have all the codecs I could possibly need, including potential fixes for Lucid described on page 151. Still not working. It allowed me to notice that all streaming video were showing only a black screen.

Halp

---

### Post by no2498 on 2010-05-25
have you tried setting the pic size smaller in cheese
910 up cheese  has all the settings for webcams

---

### Post by RabidFX on 2010-05-26
Yes, tried that - still a black screen.

I think it's not a webcam problem but a codec problem thus. Is there a way to know which one I need ?

---

### Post by RabidFX on 2010-05-26
Some (good) news !
I reread some other threads and tried testing stuff through gstreamer-properties.

I had "autodetect" selected for video output.
Test showed only a black screen. I tried the different options, and finally ! :
With video output set to "X window system (without Xv)", the video test runs well, and testing the webcam also works (Video input was already properly set to v4l2.)

Webcam also shows on cheese, although the framerate is quite bad.
The Skype problem remains thus : Skype won't show anything in the video test.

I feel I'm getting close to a solution but could use some help.

Should I start a new thread since this is now a Skype-only problem ?

[Edit] Before anyone asks, YES I'm running Skype preloading v4l1compat.so :p

---

### Post by RabidFX on 2010-05-26
Problem solved.

The solution was right in front of me when I mentioned that video output had to be set to "X Window System (No Xv)" in gstreamer-properties.

Skype apparently want Xv badly, so that can't do, and Xv not working meant bad drivers. Proprietary graphic card drivers installed, problem solved.

I edited my first post to ease the task of people with similar problems, but couldn't add a "solved" tag instead of the "ubuntu" one. Did I miss something ?

[Edit] Ok, I lurked again :P Was in the "Thread Tools".

---

### Post by amirhomayoun on 2010-05-31
Thanks a lot! This solved my problem! 

Although I had the NVIDIA driver installed before. I just switched from "NVIDIA accelerated graphic driver (version 173)" to the "NVIDIA accelerated graphic driver (version current)" which appears to be 195.

With this driver I can use my webcam (Laptop Integrated on Dell XPS m1330, Ubuntu 10.04 Lucid, clean install). No matter what my default output plugin in my "gstreamer-properties" is. Works with all of them (I have chosen Autodetect though).

On Karmic I had no problem at all, but I don't remember the version of my driver and the settings in gstreamer back there. Hope this helps!

---

### Post by akshaya_aradhya on 2010-06-16
I was trying to get my Microsoft Lifecam VX-3000 USB Webcam working on Lucid Lynx for a long time now. Your instructions really helped me get this configured on my pc. I can now work on ubuntu as long as I want and yet manage to maintain my contacts overseas.

Thanks a lot.

---

### Post by GoRien on 2011-01-27
I just subscribe here. :)

---

