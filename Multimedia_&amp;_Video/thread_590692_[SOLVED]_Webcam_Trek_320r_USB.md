---
title: "[SOLVED] Webcam Trek 320r USB"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by Plasma_NZ on 2007-10-25
Ok.. pritty siimple...

Trying to get a USB Webcam to work.... 

Genius Trek 320r
Seem's that when i plug it in it's something else...?
any idea's on where i should head from here.?

camorama results are "/dev/video0" doesnt exist...

results of  " lsusb "

> 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 002: ID 050d:0815 Belkin Components 
Bus 001 Device 001: ID 0000:0000  


This is the same thing after i plug in the "WEBCAM" :confused:

> 
Bus 002 Device 005: ID 0458:702c KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 002: ID 050d:0815 Belkin Components 
Bus 001 Device 001: ID 0000:0000  


---

### Post by Chriis on 2007-10-27
Hi,

Here it's look like :

-> lsusb (Before plug cam)

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05e3:070e Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04a9:1062 Canon, Inc. S500 Printer
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

-> lsusb (After plug cam)

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05e3:070e Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04a9:1062 Canon, Inc. S500 Printer
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

But camorama : "Could not connect to /dev/video0"

is it possible that the Cam is set to /dev/video1 ?? 

and if yes,..  is it even possible to tell Camorama
to use /dev/video1 instead /dev/video0 ??

Thanks :)
ps: i'm new to linux,..do not hit me too hard plz :lolflag:

---

### Post by Chriis on 2007-10-27
Ask a question is almost answer it,..

camorama -d /dev/video1

And it work for me,..:guitar:

---

