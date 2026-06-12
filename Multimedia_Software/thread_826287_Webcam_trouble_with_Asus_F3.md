---
title: "Webcam trouble with Asus F3"
date: 2008-06-11
forum: Multimedia Software
---

### Post by jerkata on 2008-06-11
Hi All,

I'm relatively new to Ubuntu and linux - I just installed Hardy last week... I have an ASUS F3Useries laptop with an integrated webcam... I've installed camorama but it refuses to pick up any devices...

The output from CLI >camorama throws the error - "Could not connect to video device (/dev/video0). Check the connection."

the output from CLI >lsusb is...
Bus 006 Device 003: ID 0c45:624f Microdia 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I've even installed Cheese - but from a CLI - i get the app opening with a test screen and the error in the command prompt...
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
I've reinstalled xorg and XLib - and this hasn't helped...

If i could just get one working - i'd be happy - any advice is appreciated!!!! Thanks in advance

Jerkata

---

### Post by linuxwizard on 2008-06-11
For Microdia webcams this is the driver you need from here > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

Bus 006 Device 003: ID 0c45:624f Microdia

---

### Post by jerkata on 2008-06-12
Hi again,

Thanks for your feedback - the site looked great but the only problem is that there don't appear to be any drivers available for ubuntu 8.04...

I tried to join - but they are closed to new members... any more ideas as to where i could get the driver i need?

Thanks in advance!

Jerkata

---

### Post by jerkata on 2008-06-12
Problem solved....

[http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/)

---

### Post by caglar.dursun on 2008-10-19
> **jerkata said:**
> Problem solved....

[http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/)

The link is not correct.This is the correct one 
[http://www.indragunawan.com/2008/07/microdia-webcam-driver.html](http://www.indragunawan.com/2008/07/microdia-webcam-driver.html)

---

