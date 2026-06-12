---
title: "Webcam issues - No image feed"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by GourmetGen on 2008-02-29
Hello,
I am new to ubuntu and was trying to install my Creative Notebook Pro web camera. 

To start with I followed the procedures on this thread, 
[http://ubuntuforums.org/showthread.php?t=660463&highlight=creative+webcam]("http://ubuntuforums.org/showthread.php?t=660463&highlight=creative+webcam") 

And for a short time the webcam worked in Cheese and ekiga but not skype. 

I think I must have tried installing another driver (hoping to get it to work with Skype) and now I get no video feed but it seems to be recognised by the system. 

When I open Cheese, I get "unable to find webcam, sorry". When I open Ekiga, Camera Monitor tells me the camera is on, but ekiga shows a black screen with Standby underneath.

I hope that someone can help. 

lsusb brings up this:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 041e:4061 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  

lsmod:
ov51x_jpeg            154360  0 
videodev               29312  1 ov51x_jpeg
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

Thank you

---

### Post by pjbgravely on 2008-03-02
First try the program cheese.
 sudo apt-get install cheese 

If that doesn't work, unplug the cam, replug it in and open a terminal and type 
dmesg|tail

and copy the output here.

Paul

---

### Post by GourmetGen on 2008-03-03
Hi,
The newest version of cheese is already installed. 

dmesg|tail brings up:

[142056.484000] usb 1-1: USB disconnect, address 10
[142058.228000] usb 1-1: new full speed USB device using uhci_hcd and address 11
[142058.428000] usb 1-1: configuration #1 chosen from 1 choice
[142058.432000] /home/gen/webcam-driver/ov51x-jpeg-core.c: USB OV519 video device found
[142058.784000] /home/gen/webcam-driver/ov51x-jpeg-core.c: Sensor is an OV7670
[142059.424000] /home/gen/webcam-driver/ov51x-jpeg-core.c: Device at usb-0000:00:1d.0-1 registered to minor 0

Is there a way to re-install the ov51x driver? Maybe that will make it work again?
Thanks,

---

### Post by pjbgravely on 2008-03-03
Sorry, I somehow got your thread confused with someone else's. I was going to say the best thing would be to do is to reinstall the driver with the instructions that worked. Make sure you remove the old driver, and rebooting afterwards some times helps. 
 
Skype beta, is just that beta and buggy. I finally found a version that works with both sound and video 2.0.0.43. You can download it from Skype, or use the medibuntu repository. If you are already using that version, then all you can do is wait. Skype is closed source so debugging takes a lot longer. 

Paul

---

### Post by GourmetGen on 2008-03-05
Thanks for the help, I'll try re-installing the driver like you said and see how it goes.

---

