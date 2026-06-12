---
title: "WEBCAM TRUST driver problems"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by anofele on 2008-02-11
I really can't get my trust webcam working. After trying numberless howtos, manually compiling the driver or everything else it still fails. Well, that's what comes out from the dmesg:

[   90.165408] /usr/src/modules/gspca/gspca_core.c: USB GSPCA camera found. (PAC207)
[   90.165437] /usr/src/modules/gspca/gspca_core.c: [spca5xx_probe:4041] Camera type GBRG 
[   90.275769] /usr/src/modules/gspca/gspca_core.c: [spca5xx_getcapability:1198] maxw 352 maxh 288 minw 160 minh 120
[   90.276146] usbcore: registered new interface driver gspca
[   90.276167] /usr/src/modules/gspca/gspca_core.c: gspca driver 01.00.16 registered
[  120.476484] /usr/src/modules/gspca/gspca_core.c: [spca5xx_open:1919] DEALLOC error on spca50x_init_source
[  185.776297] /usr/src/modules/gspca/gspca_core.c: [spca5xx_open:1919] DEALLOC error on spca50x_init_source

It finds it, it gets also the picture size... but then it fails... I'm really confused. 

Also the driver appears to be in 2 different places on my sys: /lib/modules/generic-VERSION**/ubuntu/media/gspcav1

and /lib/modules/generic-VERSION**/kernel/drivers/usb/media

to be sure I overwritten also the first one (wich seems unaffected by the module install script, but one tutorial said this could have been a solution....)

I assure you I did the basics right, compiling with correct headers and whatever.... I really can't get it. Seems like the driver stops working. In fact Camorama says "No device"....

Thanks all.

---

