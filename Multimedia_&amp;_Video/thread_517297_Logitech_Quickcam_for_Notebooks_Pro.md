---
title: "Logitech Quickcam for Notebooks Pro"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by bvone21 on 2007-08-04
I'm unable to find any resources for help on this, seems like webcam support is just hit or miss right now, which is odd.  I didn't even think it would be an issue at this stage but looking around for answers says otherwise.  I've got a Logitech Quickcam for Notebooks Pro, here's my device id:

> Bus 004 Device 004: ID 046d:08cb Logitech, Inc. 

the microphone works fine, i can test it fine in Ekiga, but no video.  Trying to use camorama says "Cannot connect to video device (/dev/video0/). Please check connection."

lsmod shows:
> 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev

does this mean i'm using UVC?  Is this something I need to switch.  I'm trying to learn but I'm pretty much a noob.  This may sound dumb also...could it be that the camera isn't on video0? but something else? how can i check this.

thanks for any help, it works just fine in windows so i've been rebooting into xp to actually use it, which is a hassle since I've been sticking to ubuntu day to day normally.

---

### Post by bvone21 on 2007-08-05
Woot! I'm staring at myself in Ekiga right now, so I must have done something right.

I followed this here to install the UVC driver [https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)

I know that's an old how to, i just subsituted the latest version of the driver and followed that...very simple and it works... I know it looks like my pc was already using UVC, so I'm not sure why it didn't work before, I've recently upgraded to Gutsy maybe that's why a reinstall of the driver was needed?  I'm not really sure, but just thought i'd post this in case someone searches and finds my similar problem.

---

### Post by garoth2 on 2007-11-09
I just had some success with the Quickcam for Notebooks Pro (046d:08cb)

There's some kind of firmware bug in this camera that for some reason makes it incompatible with the timing of the EHCI controller. The workaround for this is to get the device to run in full-speed mode.

I couldn't figure out how to force the device to run in full-speed mode instead of high-speed mode - so if anyone knows how to do this that would be helpful.

What I did was dig up an old USB hub I had, that gets detected as a full-speed device, and plugged the camera into that - voila it works (in Ekiga).

---

