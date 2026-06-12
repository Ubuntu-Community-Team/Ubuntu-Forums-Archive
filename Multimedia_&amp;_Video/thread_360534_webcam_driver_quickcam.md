---
title: "webcam driver quickcam"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by wxnker on 2007-02-13
My **Logitech quickcam communicate STX usb 1.1** is kinda working in Ubuntu Edgy out of the box.

**[COLOR="Red"]Where can I see which drivers the webcam is using?[/COLOR]**

If I look under my kernel /lib/modules/2.6.17-11-generic/kernel/drivers/media/video folder there are different possibilities but I have no clue which driver the webcam is using and a command like lsusb does not tell anything about this.

_Here are some of the folders:_
quickcam/quickcam.ko
usbvideo/ibmcam.ko, ultracam.ko and more...
spca5xx/spca5xx.ko

_lsusb output:_
[COLOR="Gray"]$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  [/COLOR]

I was considering updating spca5xx to try to improve webcam quality, but I'm not even sure that this is the driver that the logitech webcam is using since I never installed a driver. I just plugged the cam in Ubuntu Edgy and it worked, although the quality is not very good.
 **[COLOR="Red"]Which "standard" driver does Ubuntu Edgy use?[/COLOR]**
[B]
BTW[/B]: Isn't there any tool/gui to use for webcam (global) settings like light and contrast? By global I mean standard settings for the webcam to use in other apps like camorama and AMSN.

**Sorry for doubleposting. *DOH***

---

