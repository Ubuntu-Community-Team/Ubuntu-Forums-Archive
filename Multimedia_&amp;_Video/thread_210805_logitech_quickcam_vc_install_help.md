---
title: "logitech quickcam vc install help"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by screamingindigital on 2006-07-07
hello all...i am currently running dapper and everything is running great except my webcam.  i have a logitech quickcam vc (round, black usb model) and i cannot get this thing installed.  i have downloaded the drivers from [here]("http://digilander.libero.it/demarchidaniele/qcamvc/quickcam-vc.html") but i get errors (make, make install will not work)  here is a c/p from the install howto: ](*,) 

To use with 2.6.x kernels:
---------------------------------------------------------------------------

The 2.6 kernel modules are contained in the linux_2.6 directory.

'cd linux_2.6'
'make' will display a list of instructions.
'make modules' builds the drivers
'make install' installs the drivers as modules

'modprobe qcamvc_pp' if you have the PP QuickCam
'modprobe qcamvc_usb' if you have the USB QuickCam

Read the notes below on getting the best performance from the parallel port
version of the camera, using DMA transfers.

-------------------------------------------------------------------------

any help out there??

Thanks
;)

---

### Post by Rackerz on 2006-07-07
[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) - That driver works for a lot of webcams, might be worth trying.

---

