---
title: "multiple usb video cameras via usb extender and usb hub"
date: 2010-12-03
forum: Multimedia Software
---

### Post by Slates on 2010-12-03
Im trying to run multiple usb webcams as part of a monitoring system on Ubuntu 10.4. I need to use a usb hub as I only have two usb ports, only one of which can be freed up.

I have done this successfully, connecting 4 webcams, all logitec, two different types. These run up in cheese, xawtv and the video monitoring application. 

However having 4 cameras close to my ubuntu system is not particularly useful. So I put one webcam on a usb extender. This does not work when connected via the usb hub (see below). By this I mean I cannot get cheese or xawtv to work with it, cheese simply doesnt start up, xawtv generates the errors listed below. It seems strange to me that the apparent simple addition of a usb hub somehow interferes with the otherwise fine operation of a usb camera via a usb extender.

In addition if I run the same setup on windows (using Skype or Yawcam for example) it works in all situations, including a camera plugged into the usb hub with an extender. This to me points squarely at the Ubunbtu drivers, or their configuration.

Can anyone please point me in the right direction to get this working ? I dont view this as a particularly oddball request, surely any video monitoring solution would use a hub and usb extenders ?

Output from xawtv with usb hub and usb extender (but fine with either one or the other, just not both) :

> v4l-conf had some trouble,  trying to continue anyway 
Warning: Cannot convert string  "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct 
ioctl: VIDIOC_G_STD(std=0x1 [PAL_B]): Invalid argument 
libv4l2: error turning on stream: No space left on device 
ioctl: VIDIOC_STREAMON(int=1): No space left on device 
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument 
v4l2: oops: select timeout 
libv4l2: error turning on stream: Device or resource busy 
     I dont have enough expertise around this to know what the complaint about "no space left on device" is assuming thats the cause and not just a symptom. It certianly isnt a disc space issue.

---

