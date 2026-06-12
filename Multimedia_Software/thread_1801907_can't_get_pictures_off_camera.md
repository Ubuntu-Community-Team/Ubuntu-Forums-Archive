---
title: "can't get pictures off camera"
date: 2011-07-11
forum: Multimedia Software
---

### Post by netopalis45 on 2011-07-11
I recently bought a Global Point Products waterproof camera to use on vacation and after taking several pictures, I tried to connect it to my Ubuntu laptop to get the pictures off. Unfortunately, it seems that you need proprietary drivers which I failed to bring with me. Is there anything out there that I can use to extract these pictures?

---

### Post by smurphy_it on 2011-07-11
I'm guessing it uses an USB plug, and not an MMC ?

---

### Post by netopalis45 on 2011-07-11
Yes it does.

---

### Post by dog-soldier on 2011-07-11
what i did was buy a card reader to get the pictures off anything with a card. work great and have had no problems at all.

---

### Post by SoFl W on 2011-07-11
With the camera plugged in to a usb port,* powered on*, type "lsusb" in terminal and post the results.  It *might* need to also be plugged into a power outlet as if you are recharging it.

---

### Post by netopalis45 on 2011-07-11
Did what you said. Text file with output is attached.

---

### Post by handy on 2011-07-13
If the camera has a removable memory card, just stick it into a card reader & you are away (which many consider the safest way - for your camera - anyway).

If it doesn't have a memory card, have you tried doing what SoFl W said & plugged the power supply into in the hope that it just wants a better power supply, & then plugged the USB cable in to see if it can be mounted?

---

### Post by gandaran on 2011-07-13
some cameras have an option that you have to enable to mount as usb hard drive when plugged in the PC, check the camera settings.

---

### Post by netopalis45 on 2011-07-13
As far as I can tell this camera doesn't have any settings on it. All it has is a small LED screen to show how many pictures have been taken.

---

### Post by netopalis45 on 2011-07-16
The camera does show up in Shotwell but when I select it, I get the error "Unable to fetch previews from the camera: Unsupported operation (-6)". Not sure if that will help any.

---

### Post by SoFl W on 2011-07-16
According to your text file:
"Bus 002 Device 002: ID 2770:905c NHJ, Ltd Che-Ez Snap SNAP-U/Digigr8/Soundstar TDC-35"

See these threads:
[http://michael-peeters.blogspot.com/2009/08/getting-digital-camera-working-under.html](http://michael-peeters.blogspot.com/2009/08/getting-digital-camera-working-under.html)
[http://ubuntuforums.org/showthread.php?t=435463&highlight=argus](http://ubuntuforums.org/showthread.php?t=435463&highlight=argus)


See if those help

---

### Post by netopalis45 on 2011-07-16
Thank you. That first link worked perfectly.

---

### Post by SoFl W on 2011-07-16
Great!   (Please go to "Thread Tools" at the top and mark as solved.)

---

