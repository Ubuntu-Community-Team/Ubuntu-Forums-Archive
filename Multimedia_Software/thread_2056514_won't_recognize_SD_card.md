---
title: "won't recognize SD card"
date: 2012-09-11
forum: Multimedia Software
---

### Post by gychang on 2012-09-11
loving the latest 64bit 12.04, works well.

I have a USB card reader from my digital camera but refuses to mount, am fairly new at linux, can someone help me out?

gychang

---

### Post by Geffers on 2012-09-11
> **gychang said:**
> loving the latest 64bit 12.04, works well.

I have a USB card reader from my digital camera but refuses to mount, am fairly new at linux, can someone help me out?

gychang

Try plugging it in and rebooting computer.

Geffers

---

### Post by gychang on 2012-09-11
> **Geffers said:**
> Try plugging it in and rebooting computer.

Geffers

tried it, without success.

---

### Post by stevem531 on 2012-09-12
Something you could try if you are still having trouble and have not already done so. 

Whilst the camera card reader is plugged in, open up a terminal window and type the following at the prompt :-

$lsusb

Hit return and you should see your camera/card reader listed as one of the devices. If is does, then it at least verifies that there is basic connectivity.

If not, I would see if the camera still works OK on another PC, and try connecting a different device to the USB port of the computer just to verify that it is still functioning.
 
On my digital camera there is a mode setting to allow direct printing via USB but the setting has to be changed back again to 'Computer' in order to load photos on to the PC. I have forgotten to do so on odd occasions ;).

Let us know how you get on.

Stephen

---

### Post by bestdarncomputers on 2012-09-12
update and check for additional drivers.

---

### Post by gychang on 2012-09-13
> **stevem531 said:**
> 

$lsusb

Hit return and you should see your camera/card reader listed as one of the devices. If is does, then it at least verifies that there is basic connectivity.

If not, I would see if the camera still works OK on another PC, and try connecting a different device to the USB port of the computer just to verify that it is still functioning.

Let us know how you get on.

Stephen

Stephen: 

with lsusb, I get this so it is loading.

Bus 001 Device 007: ID 058f:6332 Alcor Micro Corp. Multi-Function Card Reader
apa@naked:~$ 

I got the card reading fine on win7 PC and download pictures fine.  so it does seem like ubuntu problem.

gychang

---

### Post by gychang on 2012-09-13
> **bestdarncomputers said:**
> update and check for additional drivers.

followed and no luck so far.

gychang

---

### Post by gychang on 2012-09-13
not sure which steps helped but now I see it in the nautilus.  I am able to d/l pictures using gthumb.

thanks to all.

gychang

---

