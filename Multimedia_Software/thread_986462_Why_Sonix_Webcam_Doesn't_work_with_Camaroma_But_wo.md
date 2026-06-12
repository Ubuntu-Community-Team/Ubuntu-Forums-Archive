---
title: "Why Sonix Webcam Doesn't work with Camaroma But works with Cheese"
date: 2008-11-18
forum: Multimedia Software
---

### Post by caglar.dursun on 2008-11-18
Hi everyone , I have some strange problem.I'm using uvcvideo driver on Asus F3S series laptop.But I have serious problem with my webcam.The problem is my webcam works with Cheese but doesn't work with camaroma and vlc media player.Here is the some information

$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 


luvcview
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 22.
 Init v4L2 failed !! exit fatal


I guess the important point is v4l2 failed.How could it be possible cheese works with correctly (except upside down image) but camaroma doesn't.What's the reason of this case and how can i fix this issue.

Owww by the way my kernel version is 2.6.24.Is this about kernel support v4l2 ?

---

### Post by trickytrickytricky on 2008-11-19
I am trying to use a Creative Live IM cam with Hardy. I couldn't get any joy out of it at all until somebody on here pointed me towards a french program called Easycam that installs drivers for many webcams. Since then the cam works perfectly with cheese but on camorama the picture is split into three idectical distorted black and white pictures.

I am trying to use it on a chat website (I think this means that it should work with flash?) Before easycam my webcam wouldn't function at all on the site, after webcam it responds but my picture is completely blacked out.

---

