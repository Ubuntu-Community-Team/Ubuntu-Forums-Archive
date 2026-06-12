---
title: "libv4l2 &amp; VIDIOC_DQBUF error : No such device"
date: 2012-08-01
forum: Multimedia Software
---

### Post by serhancan on 2012-08-01
I have written a python code by using OpenCV library to detect a motion. If a motion occurs, it takes a snapshot of the moving object and saves it. However my problem is this: 
If I execute the program on my PC (Ubuntu 12.04) everything's OK. But when I execute the program on my BeagleBone which has Angstrom Linux running and an Us Robotics webcam device attached to it, after a while it gives the following error:

libv4l2: error dequeuing buf: No such device
VIDIOC_DQBUF: No such device

How can I solve this problem? 
Regards

edit: Now I installed Ubuntu 12.04 to the BeagleBone and checked if my python code is working, it is working OK. So it seems like this problem is related to my Angstrom image. Can it be related to my libv4l2 library or my webcam's driver?

Also, if I try once more to execute the code after it gives no such device error, I get the following error:

HIGHGUI ERROR: V4L: index 0 is not correct!
OpenCV Error: Bad argument (Array should be CvMat or IplImage) in cvGetSize, file /OE/angstrom-v2012-05/build/tmp-angstrom_v2012_05-eglibc/work/armv7a-angstrom-linux-gnueabi/opencv-2.3.1-r3/opencv/modules/core/src/array.cpp, line 1238
Traceback (most recent call last):
  File "movementtracker.py", line 117, in <module>
    t.run()
  File "movementtracker.py", line 25, in run
    frame_size = cv.GetSize(frame)
cv2.error: Array should be CvMat or IplImage

It seems like, it really cannot find my webcam. So I checked the dmesg output:


[    5.234100] CPSW phy found : id is : 0x7c0f1
[    5.234863] PHY 0:01 not found
[    5.261016] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.744689] gspca_main: v2.14.0 registered
[    5.766235] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[    5.931457] gspca_sn9c20x: MT9M111 sensor detected
[    5.931884] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input0
[    5.961883] usbcore: registered new interface driver sn9c20x
[    8.137237] usb 1-1: USB disconnect, device number 2
[    8.232116] PHY: 0:00 - Link is Up - 100/Full
[    8.232360] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.411468] usb 1-1: new high-speed USB device number 3 using musb-hdrc
[    8.553771] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[    8.553771] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    8.553802] usb 1-1: Product: USB20 Camera    
[    8.554931] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[    8.572174] gspca_sn9c20x: MT9M111 sensor detected
[    8.572570] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input1
[   18.531402] eth0: no IPv6 routers present
[   27.369262] usb 1-1: USB disconnect, device number 3
[   27.641540] usb 1-1: new high-speed USB device number 4 using musb-hdrc
[   27.784057] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[   27.784088] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   27.784118] usb 1-1: Product: USB20 Camera    
[   27.785247] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[   27.803649] gspca_sn9c20x: MT9M111 sensor detected
[   27.804107] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input2
[   29.746307] usb 1-1: USB disconnect, device number 4
[   30.021423] usb 1-1: new high-speed USB device number 5 using musb-hdrc
[   30.163848] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[   30.163879] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   30.163909] usb 1-1: Product: USB20 Camera    
[   30.165008] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[   30.182342] gspca_sn9c20x: MT9M111 sensor detected
[   30.182739] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input3
[   38.291778] usb 1-1: USB disconnect, device number 5
[   38.571563] usb 1-1: new high-speed USB device number 6 using musb-hdrc
[   38.713775] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[   38.713806] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   38.713836] usb 1-1: Product: USB20 Camera    
[   38.716918] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[   38.733673] gspca_sn9c20x: MT9M111 sensor detected
[   38.734039] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input4
[   39.668029] usb 1-1: USB disconnect, device number 6
[   39.941436] usb 1-1: new high-speed USB device number 7 using musb-hdrc
[   40.083923] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[   40.083953] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   40.083984] usb 1-1: Product: USB20 Camera    
[   40.087097] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[   40.105346] gspca_sn9c20x: MT9M111 sensor detected
[   40.105804] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input5
[   44.143188] gspca_sn9c20x: Set 160x120
[   44.584686] usb 1-1: USB disconnect, device number 7
[   44.861572] usb 1-1: new high-speed USB device number 8 using musb-hdrc
[   45.003936] usb 1-1: New USB device found, idVendor=0c45, idProduct=6242
[   45.003967] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   45.003997] usb 1-1: Product: USB20 Camera    
[   45.007263] gspca_main: sn9c20x-2.14.0 probing 0c45:6242
[   45.025970] gspca_sn9c20x: MT9M111 sensor detected
[   45.026428] input: sn9c20x as /devices/platform/omap/musb-ti81xx/musb-hdrc.1/usb1/1-1/input/input6


According to this, I plugged the webcam 7 times. But I did not. My connection with the webcam breakes after executing the python code. Any ideas?

---

### Post by smontgomerie on 2013-05-24
Did you ever manage to find a solution to your problem? I'm seeing the same thing with a webcam on Android.

---

