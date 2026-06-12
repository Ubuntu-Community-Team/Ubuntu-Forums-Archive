---
title: "Problem With Web Cam"
date: 2009-04-16
forum: Multimedia Software
---

### Post by ravi_buz on 2009-04-16
I have frontech web cam and when i connect it ubuntu doesnt detect it . I started comoroma and it said "could not connect to video device(dev/video0) please check connection".But when i start a software camera monitor it says camera is on.
my lsusb output

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0c45:613c Microdia 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

i tried easycam,cheese but  no use ,

---

### Post by MikeMiracle on 2009-09-19
Are you able to make any progress with this issue?

Seems, I am facing a similar issue.

[http://ubuntuforums.org/showthread.php?t=1269970](http://ubuntuforums.org/showthread.php?t=1269970)

---

### Post by no2498 on 2009-09-20
gstreamer-properties


in the terminal

if the cam comes on ok

or click video try v4l1 or v4l2

---

### Post by psaxena on 2009-09-22
I'm facing the same problem as well. Bought an Enter webcam today..

$ lsusb
Bus 003 Device 004: ID 0c45:614a Microdia

on running any program it says that /dev/video0 directory is not found...
I've tried the procedure on google groups.. [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs) still not working

---

### Post by srivathsa.rao on 2009-11-21
hi guys..
i got partially(40% i guess) working driver using "v4l-dvb"..
no lights,output is distorted...
this is due to same bridge but diffrent sensor

> 
u need to modify the sonixj.c in v4l-dvb\linux\drivers\media\video\gspca
{USB_DEVICE(0x0c45, ***_[COLOR="Red"]0x6148[/COLOR]_***), BSI(SN9C120, OM6802, 0x34)
this line should be changed to
{USB_DEVICE(0x0c45, ***_[COLOR="Red"]0x614a[/COLOR]_***), BSI(SN9C120, OM6802, 0x34)


here the bridge is SN9C120 which is same for driverid 0x6148 also
here the sensor is ADCM6211/ADCM1700 i guess, but for 0x6148 its OM6802 which r differnet..and i dont know what is that 0x34 ..i need to analize whole code and libusb...


output is viewed using cheese...
need to test on other pids also...

---

