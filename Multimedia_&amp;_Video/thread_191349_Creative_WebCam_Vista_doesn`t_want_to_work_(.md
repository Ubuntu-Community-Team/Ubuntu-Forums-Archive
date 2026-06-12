---
title: "Creative WebCam Vista doesn`t want to work :("
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by CyberAngel on 2006-06-07
I have a Creative WebCam Vista but I cannot make it work since breezy. Now I have a fresh installation of Dapper with the same problem.

The system recognises it succesfully but it doesn`t work.

I have done the following to be sure that it is not a module problem:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-4.0
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz

cd spca5xx-20060501

sudo make CC=gcc-4.0
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```

but still no luck :(

When I am connecting the device I am getting the following from dmesg

```
[  136.781389] usb 1-6: new full speed USB device using ohci_hcd and address 4
[  136.902754] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Creative Vista VF0010 (SPCA561A)
[  136.902874] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_probe:5480] Camera type S561
[  136.909360] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_getcapability:1765] maxw 352 maxh 288 minw 160 minh 120
[  136.909592] usbcore: registered new driver spca5xx
[  136.909651] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered

```

that it seems ok but when I am trying to view video from the device it`s impossible..
I am using the program [spcaview]("http://mxhaard.free.fr/spca50x/Download/spcaview-20051212.tar.gz") and the error is the following:

```
$ spcaview -d /dev/video1
 Spcaview version: 1.1.5 date: 12:12:2005 (C) mxhaard@magic.fr
Initializing SDL.
SDL initialized.
bpp 3 format 15
Using video device /dev/video1.
Initializing v4l.
ERROR opening V4L interface
: No space left on device

```

And dmesg when I am trying to access the device is the following:

```
[  224.814496] /home/cyber/spca5xx-20060501/drivers/usb/spca561.h: [spca561_init:497] Find spca561 USB Product ID 403b
[  225.005748] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: init isoc: usb_submit_urb(0) ret -28
[  225.005849] /home/cyber/spca5xx-20060501/drivers/usb/spca5xx.c: [spca5xx_open:2437]  DEALLOC error on init_Isoc
[  225.005851]

```

Also the other programs such as amsn can`t even see that the device exists.

---

