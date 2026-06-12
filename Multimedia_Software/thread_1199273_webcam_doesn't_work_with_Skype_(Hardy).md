---
title: "webcam doesn't work with Skype (Hardy)"
date: 2009-06-28
forum: Multimedia Software
---

### Post by ManoloM on 2009-06-28
Hi there,

I have a Microsoft Lifecam NX-6000 USB webcam which works with luvcview and ekiga but can't get it to work with cheese or skype.

I am running Hardy 8.04 on a Dell Latitude D830 laptop.
This is what I get when I type lsusb:

manuel@johnson-miranda-laptop:~$ lsusb
Bus 007 Device 002: ID 045e:00f8 Microsoft Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:c018 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

So it looks like its detecting the webcam as ID 045e:00f8 Microsoft Corp.

This is what I get when I type lsmod | grep videodev:

videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev

This is what I get when I type luvcview:

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 

The webcam works here! 

Now, I installed EasyCam+Cheese but it didn't work at all. When I tried the Skype webcam test it didn't work either. I thought I screwed up by installing EasyCam so I removed it, but still no results. Why does it work with luvcview but not with cheese? How can I get it to work with Skype?

Finally when I go to System->Preferences->Hardware Information menu I find "Microsoft? LifeCam NX-6000", but I'm not sure if this came straight out of the box or if it was created by EasyCam when I installed it.

Any help will be much appreciated.

Manuel

---

