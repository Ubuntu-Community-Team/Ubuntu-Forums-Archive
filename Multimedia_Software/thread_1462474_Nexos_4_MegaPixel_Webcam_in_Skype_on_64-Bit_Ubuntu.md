---
title: "Nexos 4 MegaPixel Webcam in Skype on 64-Bit Ubuntu Howto"
date: 2010-04-25
forum: Multimedia Software
---

### Post by mazadillon on 2010-04-25
I bought this cheapy little webcam and it didn't work 'out of the box' with Skype and I had to do a bit of tweaking to get it to work. Thought I'd share how I managed to do it in order to help anyone who has a similar webcam.

lsusb:

Bus 002 Device 003: ID 0c45:6270 Microdia PC Camera (SN9C201 + MI0360/MT9V011 or MI0360SOC/MT9V111) U-CAM PC Camera NE878, Whitcom WHC017, ...

I think a default driver is loaded for this device automatically but it doesn't really work, what you really need is the microdia driver from here: [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)

Follow the instructions here to install the driver: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

Assuming all that worked and you now have your webcam working with mplayer you just need the final tweak to get it working in skype, you need to launch Skype with the following command in order to get it to work:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

It really is that simple!

Hopefully this should save some people all the effort I had to go through to find the basic steps which led me to this point!

---

