---
title: "Problems with built in webcam dell SP2208WFP monitor"
date: 2011-02-06
forum: Multimedia Software
---

### Post by joa-san on 2011-02-06
I am new to ubuntu and I have a problem with my webcam and mic built in Dell SP2208WFP monitor. I have installed ubuntu 10.10 and does not recognize or do not get to work. This is the result of lsusb command: 

joa-san@Honshin:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam
Bus 001 Device 002: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Detect my webcam as OmniVision, look for drivers for the brand, and install the uvc package. At first it worked but after reboot no longer recognize the webcam and mic. Then, uninstall the packages uvc, and I re-installed, and returned to work, but after rebooting stopped working again. I do not know what I can do to fix it. Any suggestions? Thank you very much.

---

### Post by no2498 on 2011-02-07
what program you trying the cam in/with
lets see if xawtv sees your cam
look in your package manager for it xawtv
or the software center
and you may try cheese 
full name is cheese webcam booth but should be listed as cheese

---

### Post by BicyclerBoy on 2011-02-07
Because the webcam works under some circumstances..

If you plug the webcam in after booting...does the web cam work ?

You could compare the dmesg & lsmod output for the two use cases you tabled.
Or for post boot webcam plugin. 

i.e. what changes between UVC installed fresh & then rebooting ?

AFAIK this kind of behaviour is caused by a device driver grabbing a device it should not.
You can find this in the above std output comparison.
Maybe then a blacklist or rmmod/ismod will allow a fix...

---

### Post by joa-san on 2011-02-09
I tried both programs and don't work. Thanks anyway

---

### Post by joa-san on 2011-02-09
> **no2498 said:**
> what program you trying the cam in/with
lets see if xawtv sees your cam
look in your package manager for it xawtv
or the software center
and you may try cheese 
full name is cheese webcam booth but should be listed as cheese

I tried both programs and don't work. Thanks anyway.

---

### Post by joa-san on 2011-02-09
> **BicyclerBoy said:**
> Because the webcam works under some circumstances..

If you plug the webcam in after booting...does the web cam work ?

You could compare the dmesg & lsmod output for the two use cases you tabled.
Or for post boot webcam plugin. 

i.e. what changes between UVC installed fresh & then rebooting ?

AFAIK this kind of behaviour is caused by a device driver grabbing a device it should not.
You can find this in the above std output comparison.
Maybe then a blacklist or rmmod/ismod will allow a fix...

Thank you very much for your answer, but im really new to ubuntu and I dont know what does mean all the information from the dmesg & ismod command. The webcam doesn't work if I plug it after booting. What do i have to look to find what's wrong?

---

### Post by BicyclerBoy on 2011-02-09
Don't have any further ideas except give up..

It is very strange the webcam worked after uvc install..& the webcam not working when plugged in after reboot.

Sorry.

---

### Post by no2498 on 2011-02-09
if you have the driver installed
rerun dmesg

then retry xawtv

---

