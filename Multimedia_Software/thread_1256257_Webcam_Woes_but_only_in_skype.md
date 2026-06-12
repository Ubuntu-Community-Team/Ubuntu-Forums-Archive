---
title: "Webcam Woes but only in skype"
date: 2009-09-02
forum: Multimedia Software
---

### Post by Scarath on 2009-09-02
I have a problem with my webcam and Skype.

I have be hunting through the net, have tried loads of solutions but just cannot crack this. 

The webcam works with *amsn* and with *cheese* but will not work with skype.

My kernel is 2.6.30-1. The webcam is a creative vf0220 cheap little thing.

I think have everything I need for my webcam to work including gspcav, libv4l, etc and I know the resolution is ok for skype (640x480)

I have tried:

Setting the resolution in the skype config file to 640x480.- This leads to Skype sending no video and showing green fuzz in the 'test' section of the video options. 

If I use the command:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

With the modified config file, Skype crashes. 
Without a default config file, Skype crashes. 

It may be that the gspcav drivers do not support my webcam but I dont want to give up so any ideas, thoughts, suggestions would be great.

:confused:

---

### Post by madsmaddad on 2009-09-07
OK, I have a cheapy that works with cheese, but in Skype gives a green screen with just shadows of the objects. Cheese shows it as 464x464 resolution, Skype shows it as sn9c1xx PC camera. 

I found on Mepislovers 16309 the following but have not tried it. 

1. Boot PC into MEPIS 7.0 From cold WITHOUT the usb webcam connected.
2. Open a Konsole window (terminal) and switch to root user using the su command.
3. Do lsusb to confirm the presence of any existing usb devices.
4. Do lsmod and confirm that there are no drivers listed for videodev devices
5. Plug in the usb webcam
6. As root type lsmod
7. Look for the videodev device and note that there are probably several drivers listed.
8. Try removing one driver at a time. My webcam worked when I removed sn9c102
9. Type rmmod sn9c102
10. Now type xawtv to check if your webcam is working.
Both of my previously mentioned webcams worked correctly immediately after removing the original sn9c102 driver. Of course you will need to do this every time unless you start editing other configuration files. You can read up on how to do that elsewhere!

That might help while I continue searching for a good solution.

---

