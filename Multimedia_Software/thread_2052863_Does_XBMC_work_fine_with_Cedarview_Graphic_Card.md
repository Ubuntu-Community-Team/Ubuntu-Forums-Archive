---
title: "Does XBMC work fine with Cedarview Graphic Card?"
date: 2012-09-04
forum: Multimedia Software
---

### Post by quhan on 2012-09-04
I diy a htpc with dn2800mt motherboard..

The graphic card in board is cedarview.

I installed ubuntu with these packages following:
xorg cedarview-drm cedarview-graphics-drivers libva-cedarview-vaapi-driver crystalhd-dkms firmware-crystalhd xbmc
modify the /etc/default/grub and update-grub
in xbmc video setting, the vaapi and crystalhd is enabled.

Now I got a 1280x720 xbmc screen, I can play movie in it. but it costs cpu very much. The FPS is low as 5~15(different FPS by different Skin). the movie and sound is out of sync..

Is there someone know how to improve this issue?

---

### Post by quhan on 2012-09-06
No body know it?

---

### Post by BicyclerBoy on 2012-09-06
I would suspect that you need the latest xorg-edgers intel driver & kernel modules.
xorg-edgers will update your kernel to 3.5 & intel drivers to latest.
 
Then test va-api with "vainfo"
Test openGL with "glxgears & 
glxinfo | grep OpenGL

AFAIK OpenGL is still used for post decode processing & presentation.


After some more reading...the current cedarview is a respin of the gma500 drivers.
The xorg-edgers probably does **not** help..the gma500 stuff was never avail there.

The best advice could be to gift the cedarview atom to a windows user & wait for the new SNA based atom..

---

