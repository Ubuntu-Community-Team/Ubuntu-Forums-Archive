---
title: "Webcam hell"
date: 2009-01-24
forum: Multimedia Software
---

### Post by suityou01 on 2009-01-24
Hi,

I bought a logitech quickcam webcam as it is linux supported. Having a devil of a job setting the thing up. Found a walkthrough and followed it to the letter, on setting up the the 4vl1 drivers by compiling them from source.

Here's the thing. I can occasionally get it to work in skype, but I don't know how. If I use gstreamer-properies program and set the default video device to the usb web cam I can see myself waving. But when I go into cheese it picks up the wintv card (/dev/video0) instead of the webcam /dev/video1

Skype tells me it cannot find an overlay type or somesuch.

I am running Ubuntu 8.

Any ideas? I obviously got the drivers compiled and working as I can see myself waving, its just skype and cheese that are not picking up the default device.

Been at this for HOURS.

---

### Post by suityou01 on 2009-01-24
> **suityou01 said:**
> Hi,

I bought a logitech quickcam webcam as it is linux supported. Having a devil of a job setting the thing up. Found a walkthrough and followed it to the letter, on setting up the the 4vl1 drivers by compiling them from source.

Here's the thing. I can occasionally get it to work in skype, but I don't know how. If I use gstreamer-properies program and set the default video device to the usb web cam I can see myself waving. But when I go into cheese it picks up the wintv card (/dev/video0) instead of the webcam /dev/video1

Skype tells me it cannot find an overlay type or somesuch.

I am running Ubuntu 8.

Any ideas? I obviously got the drivers compiled and working as I can see myself waving, its just skype and cheese that are not picking up the default device.

Been at this for HOURS.


This is the second MAJOR problem I have had with Ubuntu this week, and the second time I have posted in the Ubuntu forum, and the second time I have had no response.

Is Ubuntu no longer supported? Has the credit crunch bitten the Ubuntu project.

I switched to Ubuntu two years ago as I was fed up with Microsoft and things like DRM and such. Recently I have purchased hardware AFTER checking if it was Linux (and especially Ubuntu compliant) and when I got the hardware home have followed the walkthroughs to the letter and got precisely nowhere.

I am spending hundreds of pounds on hardware that is supposed to be Ubuntu friendly and yet have had no luck and am getting throughly hacked off.

I turned to the forums for help, and get ignored.

Just what is going on? Why does no one bother any more? Is Ubuntu finally dead?

---

### Post by BentSlightly on 2009-01-28
> **suityou01 said:**
> 

I am spending hundreds of pounds on hardware that is supposed to be Ubuntu friendly and yet have had no luck and am getting throughly hacked off.

I turned to the forums for help, and get ignored.

Just what is going on? Why does no one bother any more? Is Ubuntu finally dead?

I know exactly how you feel, and the Bug Report that is apparently the "solution" is almost illegible in respect to coherence, and it is also for a previoius version of Ubuntu. 

I don't think Ubuntu is dying, but I am certainly wondering why someone hasn't at least added the correct file to a repository, for download. Hunting around on Linux Blogs is the equivalent of shooting up Heroin with a needle and a spoon you found in a sewer. 


ARGHHHHHHHHH Frustrated. :popcorn:

---

### Post by krlhc8 on 2009-03-05
I open up Skype with the following command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

