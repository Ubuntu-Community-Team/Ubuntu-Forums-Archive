---
title: "logitech quickcam notebook pro webcam"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by Nim on 2007-01-12
Please please help me,

I'm a really basic ubuntu user. I bought the above webcam as I was told it was compatable and have been trying for ages to get it to work to no avail.

When I type in lsusb it says:


Bus 004 Device 002: ID 046d:08cb Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
 

and when I try to open camorama it doesn't find a video device.

I really don't know what to do. I'd appreciate it if any help you give is written in idiots terms! 

Thank you in advance!

---

### Post by Nim on 2007-01-13
Please help me.

I realise this is probably a really annoying question but I'm really stuck, any help would be grately appreciated! 

Thanks.

---

### Post by aussiebloke on 2007-01-16
Hi Nim
Seems you know more than me, I only installed today.

I also would love to know just how I can use my web-cam as above?

I get a message that I am firewalled or behind a router.

I don't have a firewall that I am aware of.

I do have a router, however as per help, I have opened a port for amsn.

I can't even get the mic on the camera to work, mind you I haven't a clue what I am doing???](*,) 

It don't work mate.:twisted:   Where is all the excellent help I was told was available on this forum?

---

### Post by aussiebloke on 2007-01-16
Come on fellas, I don't want to revert to windows.

---

### Post by sedrak on 2007-01-21
Dear Nim,

I got exacrly the same problem with webcam.

lsusb gives me

Bus 005 Device 003: ID 046d:08c3 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 046d:c510 Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000

while device is unvisible. 
Did you managed to solve a problem? Please let me know.
Thank you in advance!



> **Nim said:**
> Please please help me,

I'm a really basic ubuntu user. I bought the above webcam as I was told it was compatable and have been trying for ages to get it to work to no avail.

When I type in lsusb it says:


Bus 004 Device 002: ID 046d:08cb Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
 

and when I try to open camorama it doesn't find a video device.

I really don't know what to do. I'd appreciate it if any help you give is written in idiots terms! 

Thank you in advance!

---

### Post by kjazz16 on 2007-02-07
same issue here with my logitech quickcam pro for Notebooks. lsusb gives me same devide ID as above. I could not find a driver for it. Anyone who has a working driver for this device , PL post

---

### Post by luiverco on 2007-02-14
I found this website that claims that it supports this webcam

[http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC](http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC)

The installations instructions are here:
[http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationOfPWC](http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationOfPWC)

They don't seem newbie friendly but at least it's something

M

---

### Post by seeklinux on 2007-04-21
I have a *QuickCam for Notebooks Deluxe* and I got it working by getting the driver from [Michael Xhaard's site]("http://mxhaard.free.fr/spca5xx.html"). The supported camera page there lists the QC for Notebook Pro among many others. 

After following instructions to build and install the driver, I was able to get my camera working with **Ekiga** softphone (already installed with Feisty) and **gqcam** (I had to install this using synaptic). **camorama** did not work well (I may look bad but I do not have blue face).

---

### Post by elif81 on 2008-05-13
I got it working without having to install anything! I am using Ubuntu 8.04, and lsusb recognized the camera as 046d:08cb. So I installed Ekiga, went through the configuration. Everything worked without having to install additional drivers. Great!! This is how it should be. I haven't tried Camorama.

---

