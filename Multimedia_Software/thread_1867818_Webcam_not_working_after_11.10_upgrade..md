---
title: "Webcam not working after 11.10 upgrade."
date: 2011-10-23
forum: Multimedia Software
---

### Post by rleahey14 on 2011-10-23
I've searched around for an answer and found nothing.  

My webcam worked worked with both cheese and skype since version 9.10.  I recently updated to 11.10 and my webcam is not found anymore.  It worked while I was upgrading because when it had me choose a picture for my profile the webcam was an option and did work.  But, now that I have tried using it for both cheese and skype it works for neither.

Here is my information:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam**
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

It shows up here but /dev/video0 does not work. 

I tried all of the options in gstreamer-properties but it does not work there.

Cheese - No Device Found

---

### Post by rleahey14 on 2011-10-23
Alright I was able to solve the problem.  For those of you having a similar problem try this.

Go to the Ubuntu Software Center.  Search for Webcam.
On the bottom you have an option to show technical items.  Make sure they are showing.
Look for the package** libwebcam0** - install it. 
Restart - I am using a laptop with a built in webcam - the light blinks when you restart to show that it is working.

It is now working with both Cheese and Skype.

---

### Post by geiroffenberg on 2011-12-24
tried it, turned out i already had that installed, so that wasnt the problem.
My cam is a creative optia live something.
Some forum said it was a problem in the new kernel and it affects many webcams. 
What finally worked for me was to go all the way back to the 2.6.38 kernel (had to install it), and boot ubuntu 11.10 bu holding shift during startup until grub menu shows. 
It didnt work at first, but i installed webcamstudio and run the cam trough it one time. dont ask me why it needed  to run trough webcamstudio, but i got the tip from another thread 
After that it works as normal, except theres no preferences for the cam anywhere.

---

