---
title: "Chicony CMN5733 Webcam Driver"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by abrichr on 2007-08-20
I have a Chicony CMN5733 Camera built in to my Compal HEl80 laptop.  I'm trying to get the webcam to work.  Here is the output of lsusb:

Bus 005 Device 007: ID 0951:1603 Kingston Technology 
Bus 005 Device 005: ID 10fd:0535 Anubis Electronics, Ltd 
Bus 005 Device 003: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c518 Logitech, Inc. 
Bus 001 Device 004: ID 0a5c:2101 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

Doesn't seem as if any of these are the one I'm looking for.  I tried installing easycam2, but it tells me that no cameras were detected.  Any suggestions?

---

### Post by airstrike on 2007-08-27
I'm also trying to install my built-in camera on my compal hel80, but i haven't had any luck so far. here's my output from lsusb:

```
Bus 005 Device 002: ID 0c45:624f Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
```

microdia seems to be bluetooth related and authentec the fingerprint scanner device. that logitech entry is definetely the usb g5 mouse.

if you happen to find a solution, please let me know! it's basically the last thing i need to get done on this laptop to get it working to its fullest.

---

### Post by vivalant on 2007-08-27
This webcam is supported by the driver at
[http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by siralphred on 2007-08-27
> **vivalant said:**
> This webcam is supported by the driver at
[http://www.linux-projects.org](http://www.linux-projects.org)

thanks a million i downloaded the deb file and now my hp dv 6000 webcam works

---

### Post by reakin on 2007-11-23
Do you know which fille the driver is in on that website?  I can't find anything with a specific name related to the Hel80 or Chicony webcam.  

Has anyone gotten the webcam on the Hel80 to work in linux?

regards,
rich

---

### Post by cdawg on 2008-03-28
I am trying to get this working as well, it would seem that the microdia device is in fact the camera. The linux-projects says:

The Generic Microdia-SN9CXXX Video4Linux1 & Video4Linux2 driver is THE ONLY driver supporting (almost) all the SN9CXXX PC Camera Controllers. It works out of the box with all the existing video applications for Linux!

this implies to me that that is the device in lsusb. im going to try to install the .deb on my debian machine to see if it works.

---

### Post by reakin on 2008-03-28
I also just installed the .deb file for feisty, but now I'm a little unsure what to do.  I try:

modprobe sn9c102

and I get:

FATAL: Module sn9c102 not found.


I'd love to here your results, cdawg. Or if anyone knows what steps I'm missing.. thanks

rich

---

### Post by cdawg on 2008-04-03
Well after all that I wasent able to install the .deb because Im running Debian and running a newer kernel version. 

Does anyone know any other locations? perhaps with the binary driver in a tar.gz instead of a .deb?

---

