---
title: "Logitech, Inc Cam"
date: 2008-07-15
forum: Multimedia Software
---

### Post by solracsuii on 2008-07-15
Genius Logitech cam VideoCam Trek:
```
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:6007 Microdia 
Bus 001 Device 002: ID 046d:c03d Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```


it seems all is working :

```
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
	driver                  : "sn9c102"
	card                    : "SN9C1xx PC Camera"
	bus_info                : "usb-0000:00:0b.0-7"
	version                 : 1.1.47
	capabilities            : 0x5000001 [VIDEO_CAPTURE,READWRITE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
	index                   : 0
	name                    : "Camera"
	type                    : CAMERA
	audioset                : 0
	tuner                   : 0
	std                     : 0x0 []
	status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
	index                   : 0
	type                    : VIDEO_CAPTURE
	flags                   : 0
	description             : "bayer rgb"
	pixelformat             : 0x31384142 [BA81]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
	index                   : 1
	type                    : VIDEO_CAPTURE
	flags                   : 1
	description             : "compressed"
	pixelformat             : 0x30313953 [S910]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
	type                    : VIDEO_CAPTURE
	fmt.pix.width           : 352
	fmt.pix.height          : 288
	fmt.pix.pixelformat     : 0x31384142 [BA81]
	fmt.pix.field           : NONE
	fmt.pix.bytesperline    : 352
	fmt.pix.sizeimage       : 101376
	fmt.pix.colorspace      : SRGB
	fmt.pix.priv            : 8
```

 ```
lsmod |grep gspca
gspca                 643792  0 
videodev               29696  2 gspca,sn9c102
usbcore               146924  6 gspca,sn9c102,usbhid,ehci_hcd,ohci_hcd
```

```
 ls /dev/vid*
/dev/video0
```

but! when i try opening any program to use it says:

Could not connect to video device (/dev/video0)
Please check connection

any ideas on this one?

---

### Post by solracsuii on 2008-07-16
:-({|=

:arrow: is there anybody out there? lolz

---

### Post by TorokLev on 2008-09-19
Hi,

I experienced exactly the same issue (with the same camera) with the exception that when I used the driver in the gutsy kernel it showed some ugly pictures. But when I installed gspca driver from sources I could not connect to camera anymore.

I believe we are left "alone" on this field.

By reading other thread I had the idea to test with kopete. Yes. Kopete was able to grab some images out the camera again (before
it repeatedly died) but it was the same ugly as at the beginning.
Bad luck.

Lev

---

