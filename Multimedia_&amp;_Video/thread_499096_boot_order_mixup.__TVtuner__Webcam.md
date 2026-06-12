---
title: "boot order mixup.  TVtuner : Webcam"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by Ancient1 on 2007-07-12
Hi 

My TVtuner with TVtime works fine .  
Feisty 64bit.

However 

When my Webcam (usb, logitech's ) is connected at boot time : 
     [COLOR="Blue"] TVtime would start using the webcam ! [/COLOR]
[COLOR="DimGray"]( also , xawTV  won't start , my webcam isn't set yet ) [/COLOR]

When I boot with no WebCam , TVtime works fine 

So it seems the device number , boot order (?) is the issue

---

### Post by arang on 2007-10-21
hi man, i feel ya , i have the same problem tvtime set up to run on /dev/video0 and webcam on /dev/video1 but they mix things up at boot up and now they switch sometimes anyone got an idea about how to fix this??

im running Gutsy 7.10 32 bits

---

### Post by mgmiller on 2007-10-24
I have the exact same problem.  
If my webcam is plugged in it is assigned video0 and that is what tvtime tries to use.  

The only way to get tvtime to work is to unplug the usb webcam and reboot.  Since one device is usb and one is on the pci bus, there must be some way of forcing one or the other of them to load in a certain order.

I can't find a configuration file for tvtime that mentions which video source to use.  I could specify in there to use video1 if the webcam is plugged in.

Anyone have ideas???
:popcorn:

---

### Post by rsambuca on 2007-10-24
I get the same thing with a Hauppauge pvr150 tuner and a logitech quickcam fusion.  I use vlc to view the TV, so it isn't a big deal switching between video0 and video1.

---

### Post by mgmiller on 2007-10-24
How do you use vlc to watch tv?  
How did you configure vlc to work with your tv tuner card?
How do you make vlc scan available channels?
How do you change channels in vlc?

This could be the answer........

---

### Post by rsambuca on 2007-10-24
> **mgmiller said:**
> How do you use vlc to watch tv?  
How did you configure vlc to work with your tv tuner card?
How do you make vlc scan available channels?
How do you change channels in vlc?

This could be the answer........

It depends on what tuner card you have, but for the 150, it uses v4l2, so it is under the pvr tab in vlc.  From the command line you can use```
vlc pvr:// :pvr-device="/dev/video0"
```

I have a set-top-box with a uhf remote, so I don't use vlc to change channels - I am on the composite input.

---

### Post by mgmiller on 2007-10-24
I thought that was too good to be true.  I guess I will play around a bit with vlc and see if I can make it change channels.  I was hoping for something that had the same capabilities as tvtime, but let you select the video source.

Thanks for the quick reply.

---

### Post by rsambuca on 2007-10-24
You can change channels using the command line.

v4l2-ctl -c#

---

