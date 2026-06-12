---
title: "Kodak zd710 no longer mounts in Intrepid"
date: 2009-05-28
forum: Multimedia Software
---

### Post by artnis on 2009-05-28
Up until today my Kodak ZD710 worked out of the box in Intrepid using gThumb Image Viewer. This camera is a PTP USB camera and the storage device is a 2G SD card. 

I now get several different messages all telling me the device will not mount, there is a DBus error, etc. 

Any help will be greatly appreciated.

This issue was resolved simply by doing the following:

When the camera was plugged in to the computer USB port it was mounted immediately, and apparently appeared to be in use by that action alone. 
By unmounting the camera and then opening GThumb to import the images everything works as expected. I do not recall having to unmount the camera before this - but GThumb now works as "advertised". 

(I am using Gthumb Image Viewer - this may help with other packages like FSpot whith errors similar to the above).

---

