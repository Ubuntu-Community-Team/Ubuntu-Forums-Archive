---
title: "Howto get  my Zoran Microelectronics Digital Camera to work"
date: 2009-03-20
forum: Multimedia Software
---

### Post by joris1977 on 2009-03-20
My girlfriend got a cheap no-brand camera for free and gave it to me so she can see me when we skype...

The question is will it work on linux?

lsusb tells me:

Bus 001 Device 006: ID 0595:4343 Zoran Microelectronics, Ltd Digital Camera EX-20 DSC

dmesg gives me

[10792.112307] zr364xx: Zoran 364xx compatible webcam plugged
[10792.112320] zr364xx: model 0595:4343 detected
[10792.112326] zr364xx: 320x240 mode selected
[10792.114077] zr364xx: Zoran 364xx controlling video device 0

so that looks good, but the camera doesn't work...

skype sees no video device
camorama says: Could not connect to video device (/dev/video0). Please check connection

and in dmesg i get this error
[12743.756649] zr364xx: Failed sending control message, error -110.
[12743.756661] zr364xx: error during open sequence: 5

Does anyone know a way to make this camera work? It all looks so promising... I have been googling but haven't got any further...

---

### Post by Crunchyfrog12 on 2009-06-15
You might want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=24735](http://ubuntuforums.org/showthread.php?t=24735)

---

### Post by eschoeller on 2009-12-27
Got the same problem here ... just got an "Stealthcam: EPIC Sports Action Cam" for X-mas ... it's really just a:

ID 0595:4343 Zoran Microelectronics, Ltd Digital Camera EX-20 DSC

However, when the camera is off and I attach the USB cable, it becomes:

ID 0595:2002 Zoran Microelectronics, Ltd

Which is pretty cool, it can either connect to a PC as a USB mass storage device (the camera has an SD slot) or it can be connected as a USB webcam.

When plugged in as a webcam:
[256646.496085] usb 4-1: new full speed USB device using uhci_hcd and address 11
[256646.661352] usb 4-1: configuration #1 chosen from 1 choice
[256646.667939] usb-storage: probe of 4-1:1.0 failed with error -5
[256646.667960] zr364xx 4-1:1.0: Zoran 364xx compatible webcam plugged
[256646.667968] zr364xx 4-1:1.0: model 0595:4343 detected
[256646.667977] usb 4-1: 320x240 mode selected
[256646.668120] usb 4-1: Zoran 364xx controlling video device 0
[256647.205138] usb 4-1: Failed sending control message, error -110.
[256647.205153] usb 4-1: error during open sequence: 5

boooo, I'm getting the same error message as joris1977. The other thread referenced by Crunchyfrog12 doesn't appear to help the situation. 

Anyone have luck with this type of device?? I get a /dev/video0 but xawtv won't recognize it, and dmesg is flooded with the errors from usb4-1 repeating over and over (every few minutes)

Ah well, I didn't pay any $$ for it.

---

### Post by StivnC on 2010-01-21
Hi

I get the same error as well, I've tried the thread Crunchyfrog12 suggested and it still doesn't work.

My Camera is a Mustek DV316L and shows as

Bus 004 Device 060: ID 0595:4343 Zoran Microelectronics, Ltd Digital Camera EX-20 DSC

When it is in Web cam mode. but when I try to use Camerama I get the

Could not connect to video device (/dev/video0). Please check connection

Other Cheese Webcam Booth does not detect it either, but it does detect my laptops built in webcam which Camerama does not.

StivnC

---

### Post by eli_damon on 2010-02-18
Same problem here. I have an Oregon Scientific ATC5K connected via USB to my desktop machine running Ubuntu 9.10. It works fine when I try to mount it as a drive but not as a webcam. The troubleshooting guide for the application Cheese told me to run dmesg, which gives the following output.

[258780.536041] usb 1-1: new full speed USB device using ohci_hcd and address 7
[258780.754118] usb 1-1: configuration #1 chosen from 1 choice
[258780.758217] usb-storage: probe of 1-1:1.0 failed with error -5
[258780.758229] zr364xx 1-1:1.0: Zoran 364xx compatible webcam plugged
[258780.758234] zr364xx 1-1:1.0: model 0595:4343 detected
[258780.758238] usb 1-1: 320x240 mode selected
[258780.758322] usb 1-1: Zoran 364xx controlling video device 0
[258781.276865] usb 1-1: Failed sending control message, error -110.
[258781.276874] usb 1-1: error during open sequence: 2

---

### Post by petermck on 2010-09-04
Has anyone found a solution to this problem yet?

---

### Post by no2498 on 2010-09-05
try this


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by joris1977 on 2010-11-22
Ah just tested and camera still not works in Maverick...

It is not a problem. Loads of other cheap webcams work. 

Maybe next kernel update

[http://www.mjmwired.net/kernel/Documentation/video4linux/zr364xx.txt](http://www.mjmwired.net/kernel/Documentation/video4linux/zr364xx.txt)

who knows...

---

### Post by eli_damon on 2012-01-17
Has anyone figured out how to get an Oregon Scientific ATC5K to work as a webcam in Linux? Oregon Scientific only makes a driver for Windows, but maybe someone has figured something out.

---

