---
title: "Webcam causing usb ports to shutdown.  Moved here from ABS."
date: 2012-12-14
forum: Multimedia Software
---

### Post by skullnbones on 2012-12-14
I haven't gotten anything from Absolute beginners forum so I thought I would try here.

This is what I posted:

Ubuntu 11.10

Just bought a logitech c310 camera.   I have installed Cheese and know  that my camera does work.  The problem is that when I turn on the camera  it works but when I turn it off or try to connect to it from a website,  the rest of the usb ports shut off.  I notice this because my wireless  usb shuts down and I get no internet.  

After trying to reopen the camera Cheese says there is no device and my  wireless internet usb will not work either.  I have to reboot just to  have the usb port recognize the wireless adapter and the camera.  

Every time I try to turn on webcam it works.  I then turn off the cam  and it shuts down all usb ports.   Maybe the usb port power management  is screwy but I don't know how to change those settings.

Please help and Thank You!!!

I should add as well that my sound drivers seem to disable when before they did not.   I can usually refresh it with  'sudo /sbin/alsa force-reload' but if that doesn't work I have to reboot it all.

---

### Post by skullnbones on 2012-12-14
can anyone help??

---

### Post by skullnbones on 2012-12-16
So, for anyone that may find this handy.  From what I am seeing the usb  ports are not giving a sufficient amount of power to run my webcam,  wireless adapter and keyboard/mouse.  

Solution???  I don't know, but [http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt ]("http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt")  has some good info to change power settings to the usb ports.

Any help is still appreciated!!

There seems to be a bug:  cannot save even with sudo permissions.

---

### Post by chadk5utc on 2012-12-16
look for powered usb hub

---

### Post by skullnbones on 2012-12-16
chadk5utc, I was just looking on Amazon for them! I think that is the only way around this.  Thanks for you response!!   I really appreciate it!

---

