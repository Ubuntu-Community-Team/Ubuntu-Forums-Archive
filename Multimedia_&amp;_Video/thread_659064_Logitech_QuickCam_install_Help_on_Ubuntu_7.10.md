---
title: "Logitech QuickCam install Help on Ubuntu 7.10"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Chet Hagerbaumer on 2008-01-05
I am a newbee to Ubuntu and am having trouble getting my webcam to work with Camorama. I have a Logitech Quick Cam Express (USB) camera. When I open the Camorama program, I get a window with nothing but diagonal lines running through it. I am wondering if I might have installed the wrong drivers. But don't have enough experience to go digging through the bowels of the software.

Can someone help get me started in the right direction? I would appreciate any help you can offer.

Thanks!!!!!!!

---

### Post by linuxwizard on 2008-01-05
Which driver did you install ? in terminal type >lsusb > post results 
Also in Camorama did you try use the setting to adjust the picture ?

---

### Post by Chet Hagerbaumer on 2008-01-06
I typed in what you suggested and here is the responce.  I don't see a listing for the camera.  Now what do I do?

chet@chet-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:3002 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 0545:8333 Xirlink, Inc. 
Bus 003 Device 002: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 003 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
chet@chet-desktop:~$

---

### Post by linuxwizard on 2008-01-06
Did you have the webcam plugged in ? If you did try another USB port and type lsusb again.

---

### Post by Chet Hagerbaumer on 2008-01-07
I tried another usb port and retyped lsusb.  It is now showing up on the list of devices.

chet@chet-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:3002 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 012: ID 046d:0928 Logitech, Inc. Quickcam Express
Bus 003 Device 011: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 003 Device 002: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
chet@chet-desktop:~$ 

Ok!! It looks like the cameera is now being recognized.  What do I do next?  As I said before I am a noob.

If we can get this thing to work I will be a very happy camper.  So far we are making progress.

Thanks for all of the great support!!!!!

---

### Post by linuxwizard on 2008-01-07
Ok on this page about 1/4 way down shows your cam as working & supported.
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Did you try changing the settings in Camorama? Also try Ekiga to test it. That cam should just work by plugging it in.

---

### Post by Chet Hagerbaumer on 2008-01-09
:KS

The camera works with Ekiga sort of.  The setting slide bars have varying effects from little to no effect to extreemly sensitive  I still have no luck with Camorama.  Any ideas?

---

### Post by linuxwizard on 2008-01-09
Open Camorama > the white box under effect right click there > add filter > color correction > than try to adjust settings

---

### Post by milkyky on 2008-01-15
hi LinuxWizard,
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 

i get this after lsusb. So where should i download the driver from?thanks.

---

### Post by linuxwizard on 2008-01-15
milkyky
Just plugin the webcam you should not have to install a driver for that cam. Try using Ekiga or Camorama see if cam works. You will have to use settings to adjust brightness in those apps..

---

