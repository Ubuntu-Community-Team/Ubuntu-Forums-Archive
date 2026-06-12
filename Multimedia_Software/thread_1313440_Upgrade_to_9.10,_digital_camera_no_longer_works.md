---
title: "Upgrade to 9.10, digital camera no longer works"
date: 2009-11-03
forum: Multimedia Software
---

### Post by mysticrider92 on 2009-11-03
Hey all,
I have a Canon A620 camera that has been working perfectly under 9.04. When I plug it in, the camera screen usually goes blank and Ubuntu gives a notice that a camera is found. Then I can open it in F-spot and copy pictures over. However, after upgrading to 9.10, it seems to be acting differently. The screen does not go blank as usual. I get the notice that a camera is found, but on clicking "Import Photos", F-Spot opens then says it doesn't detect any cameras. Nautilus used to pick up the camera, but it doesn't work now either. 

There is no other error or indication of what the problem could be. Dmesg suggests that a new USB device was plugged in, but nothing about the camera itself, and lsusb doesn't show any new devices. A google search turned up nothing, so I'm wondering if someone else has has a similar problem. Thanks in advance.

---

### Post by Anon Customer on 2009-11-03
Similar problem.

Ubuntu 9.10. Canon Powershot G3. Dialog pops up when camera is plugged in and f-pot can be opened through there, but I get an error that he camera is locked. Trying to manually import from the camera in f-pot also fails with the same error.

Workaround is to unmount the camera (either through the dialog or right-click on camera icon on desktop and select Unmount) and then menually import in f-spot (Photo > Import > select camera from Import Source drop down).

---

### Post by mysticrider92 on 2009-11-04
My problem is that the camera doesn't mount at all. F-spot says that no camera was detected, nautilus doesn't pick it up at all, and lsusb doesn't show anything being plugged in. 

I've had to use that workaround occasionally with 9.04, but it won't work this time.

---

### Post by naarkhoo on 2009-11-29
I have same problem with my canon SX120 IS (canon). I am using ubuntu 9.10 ...
Is there any idea?!

---

### Post by Chronon on 2009-12-06
My Canon S5 IS doesn't mount but is detected by lsusb.  

I have resorted to putting the memory card into a card reader, which does auto-mount properly.

---

### Post by skzuk on 2009-12-31
> **Chronon said:**
> My Canon S5 IS doesn't mount but is detected by lsusb.  

I have resorted to putting the memory card into a card reader, which does auto-mount properly.

This is my situation as well. Canon S5 IS, in Xubuntu 9.10. I'd rather use the USB cable, but can't make it happen.

---

### Post by dzsobacsi on 2010-09-21
I cannot mount my Canon S5IS either however Picasa 3.0.0 recognizes it so I can download my photos. Just wait patiently after pressing the import button because there is no progress bar and the only indication that something happens is the red flashing led on the camera. 

Another option to get your photos is gPhoto2
[http://www.gphoto.org/](http://www.gphoto.org/)

Any idea to mount it properly is still appreciated.



Update:  I do not have this issue since I use Shotwell. Just works perfectly with my camera.

---

### Post by ntracs on 2011-08-10
> **skzuk said:**
> This is my situation as well. Canon S5 IS, in Xubuntu 9.10.
 
 I'd rather use the USB cable, but can't make it happen.
 
 
I also had the same problem I found out that the mini usb port on the back of the camera is slightly smaller that the USB cables.  Therefore proper contact is not make. 
 
I went thru  three cables and they all failed.  I noticed when I pushed  in the USB  cable into the camera and wiggled the cable upward the camera started working.
 
I think that the mini usb port on the back of the camera is slightly smaller than  the standard usb cables and contact is intermittent.

---

