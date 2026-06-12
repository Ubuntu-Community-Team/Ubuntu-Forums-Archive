---
title: "Logitech Quickcam IM Plus Problems"
date: 2009-08-12
forum: Multimedia Software
---

### Post by monsieurdozier on 2009-08-12
I'm trying to set up Zoneminder, and I'm having trouble with the Webcam I bought.

I bought a Logitech Quickcam IM Plus, which according to the Logitech Site should work with the SPCA 5 Driver.

So following this website: [http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/](http://www.linuxscrew.com/2007/11/05/howto-home-video-security-with-zoneminder-and-ubuntu/)

I used

sudo aptitude install gspca-source -y

After which I installed Camorama and restarted my computer.

I get the error message from Camorama, "Could not connect to video device (/dev/video0). Please check connection."

The camera is plugged in.  So here's what I get from lsusb:

Bus 001 Device 006: ID 046d:09a4 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0b38:0010  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it sees the camera. lsmod | grep gspca comes up nothing.  So I then:

sudo modprobe gspca

Which comes up:

FATAL: Module gspca not found.

So, how can I get my camera working?

---

### Post by tripolitan on 2009-08-12
-Instructions on the website you linked do not pertain to your model of webcam nor your distribution (Ubuntu 7.10 Gutsy Gibbon)
-According to LibLand's SPCA5 page, Logitech Quickcam IM Plus (046d:09a4 Logitech, Inc.)is not supported. 

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

**If you can find it, the Logitech Webcam for Notebooks works out of the box with Hardy Heron. [http://www.mrgadget.com.au/2006/11/superb-webcam-logitech-webcam-for.html](http://www.mrgadget.com.au/2006/11/superb-webcam-logitech-webcam-for.html)

---

### Post by monsieurdozier on 2009-08-12
Thanks for the response, I'll return this cam and see if I can get another one.

---

