---
title: "Getting my ICM532 chipset based webcam working"
date: 2011-03-27
forum: Multimedia Software
---

### Post by kjaggu on 2011-03-27
Hi all, 

I have a ICM532 chipset based webcam (D-Link DSB-C320). I could not find a solution across the forums to get the camera working properly for me on Ubuntu 10.10. There is a thread ([http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)) concerning the same chipset on the forums, but it is quite old. I do not want to risk breaking my system while attempting the fix. It would be really helpful if you could help me on the same. 

Also, when I check the webcam through Cheese, I get images with alternating yellow-tinge and blue-tinge.

---

### Post by no2498 on 2011-03-28
your cam should work out of the box


open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2

use the bottom test button for each 1
you may need to change the plugin to auto


this all comes from the cheese help FAQ'S

the driver is in the kernel now days

---

