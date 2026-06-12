---
title: "How to stream video from a LCD digital microscope?"
date: 2019-12-07
forum: Multimedia Software
---

### Post by sunbear-c22 on 2019-12-07
I am trying to get a digital microscope with a LCD display to work on Ubuntu 18.04. The micro-usb connector on the LCD display is connected to the computer via a USB cable. I tried using the Cheese application to work it but it does not detect it.
Below are some linux commands that I had used to extract more information on the device. The info gathered appears positive. 
**What should I do next to be able to stream images from the camera device?**

Plugging unplugging the device gave the following message in dmesg:
```
[44885.610572] usbcore: registered new interface driver snd-usb-audio
[44885.611073] uvcvideo: Found UVC 1.00 device GENERAL - UVC  (1b3f:2202)
[44885.611773] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[44885.611970] uvcvideo 1-14:1.0: Entity type for entity Processing 5 was not initialized!
[44885.611971] uvcvideo 1-14:1.0: Entity type for entity Selector 4 was not initialized!
[44885.611973] uvcvideo 1-14:1.0: Entity type for entity Camera 1 was not initialized!
[44885.612060] input: GENERAL - UVC : GENERAL - UVC  as /devices/pci0000:00/0000:00:14.0/usb1/1-14/1-14:1.0/input/input24
[44885.612152] usbcore: registered new interface driver uvcvideo
[44885.612153] USB Video Class driver (1.1.1)

[46963.597579] usb 1-14: new high-speed USB device number 14 using xhci_hcd
[46963.746118] usb 1-14: config 1 interface 0 altsetting 0 endpoint 0x84 has an invalid bInterval 32, changing to 9
[46963.746126] usb 1-14: config 1 interface 3 has no altsetting 1
[46963.746440] usb 1-14: New USB device found, idVendor=1b3f, idProduct=2202, bcdDevice= 1.00
[46963.746444] usb 1-14: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[46963.746448] usb 1-14: Product: GENERAL - UVC 
[46963.746451] usb 1-14: Manufacturer: GENERAL
[46963.748187] uvcvideo: Found UVC 1.00 device GENERAL - UVC  (1b3f:2202)
[46963.748912] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[46963.749263] uvcvideo 1-14:1.0: Entity type for entity Processing 5 was not initialized!
[46963.749266] uvcvideo 1-14:1.0: Entity type for entity Selector 4 was not initialized!
[46963.749270] uvcvideo 1-14:1.0: Entity type for entity Camera 1 was not initialized!
[46963.749456] input: GENERAL - UVC : GENERAL - UVC  as /devices/pci0000:00/0000:00:14.0/usb1/1-14/1-14:1.0/input/input25

```


From lsusb command, I found the device to be:
```
$ lsusb
Bus 001 Device 014: ID 1b3f:2202 Generalplus Technology Inc. 

```

I used the following command to list all the video devices on my system before and after plugging the device to the system:
```
$ ls /dev/video*
ls: cannot access '/dev/video*': No such file or directory
$ ls /dev/video*
/dev/video0  /dev/video1

```
I used this commands to get more iinfo on the detected video devices:
```
$ v4l2-ctl -d 0 --all
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : GENERAL - UVC : GENERAL - UVC 
	Bus info      : usb-0000:00:14.0-14
	Driver version: 5.0.21
	Capabilities  : 0x84A00001
		Video Capture
		Metadata Capture
		Streaming
		Extended Pix Format
		Device Capabilities
	Device Caps   : 0x04200001
		Video Capture
		Streaming
		Extended Pix Format
Priority: 2
Video input : 0 (Camera 1: ok)
Format Video Capture:
	Width/Height      : 1280/720
	Pixel Format      : 'MJPG'
	Field             : None
	Bytes per Line    : 0
	Size Image        : 1843200
	Colorspace        : Default
	Transfer Function : Default (maps to Rec. 709)
	YCbCr/HSV Encoding: Default (maps to ITU-R 601)
	Quantization      : Default (maps to Full Range)
	Flags             : 
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 1280, Height 720
	Default     : Left 0, Top 0, Width 1280, Height 720
	Pixel Aspect: 1/1
Selection: crop_default, Left 0, Top 0, Width 1280, Height 720
Selection: crop_bounds, Left 0, Top 0, Width 1280, Height 720
Streaming Parameters Video Capture:
	Capabilities     : timeperframe
	Frames per second: 30.000 (30/1)
	Read buffers     : 0
                     brightness 0x00980900 (int)    : min=1 max=255 step=1 default=48 value=48
                       contrast 0x00980901 (int)    : min=1 max=127 step=1 default=36 value=36
                     saturation 0x00980902 (int)    : min=1 max=127 step=1 default=64 value=64
                            hue 0x00980903 (int)    : min=-128 max=127 step=1 default=0 value=0
                          gamma 0x00980910 (int)    : min=0 max=20 step=1 default=0 value=10
                      sharpness 0x0098091b (int)    : min=0 max=3 step=1 default=3 value=3
         backlight_compensation 0x0098091c (int)    : min=0 max=127 step=1 default=8 value=8

$ v4l2-ctl -d 1 --all
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : GENERAL - UVC : GENERAL - UVC 
	Bus info      : usb-0000:00:14.0-14
	Driver version: 5.0.21
	Capabilities  : 0x84A00001
		Video Capture
		Metadata Capture
		Streaming
		Extended Pix Format
		Device Capabilities
	Device Caps   : 0x04A00000
		Metadata Capture
		Streaming
		Extended Pix Format
Priority: 2

```

---

### Post by sunbear-c22 on 2019-12-07
I came across this [article]("https://medium.com/@premek/the-smallest-webcam-under-linux-5355ee123ae0") which mentioned that there is a need to reconfigure the uvcvideo module with a quirks=2 option via commands: 
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=2
```

According to [this other article]("http://www.emmatonkin.com/ukolndev/tag/uvcvideo/"), the module uvcvideo can be permanently set with the "quirks=2" setting by creating the file `/etc/modprobe.d/uvcvideo.conf` to contain the line:
```
options uvcvideo quirks=2
```

Thereafter, I used the "vlc media player" application to open the video device "/dev/video0" and set video standard to "ALL":
First, click "Media"-->"Open Capture Device". 
Second, set "Video Device Name" to "/dev/video0" and "Video standard" to "ALL".
Third, click "Play".

To take a snap shot on the vlc media player, click the menu Tab "Video"-->"Take Snapshot". 

[B]Question: 
1. What does the "quirks=2" option mean during the "modprobe uvcvideo" command?
 2. How do I record a video from the VLC media player?[/B]

---

### Post by Holger_Gehrke on 2019-12-07
The 'modprobe' command loads kernel modules and can pass parameters to them. The 'quirks' parameter of the uvcvideo module activates various workarounds for devices that are not quite uvc-compliant. In the [headers of the module]("https://github.com/torvalds/linux/blob/master/drivers/media/usb/uvc/uvcvideo.h") you'll find the names and values for the various quirks around line 190. The parameter is treated as a bitmap, so you can simply add up the values to get the parameter value to give to the module. So a value of 2 means UVC_QUIRK_PROBE_MINMAX. According to uvc_video.c this seems to control whether the driver relies on values given by the device during initialization for minimum and maximum compression or requests those values separately (because the ones given earlier are wrong ...).

Holger

---

### Post by sunbear-c22 on 2019-12-07
@Holger_Gehrke Thank you for your explanation on 'quirks'. Very helpful. Also, I found a webpage on [Linux UVC driver and tools &#8211; FAQ]("http://www.ideasonboard.org/uvc/faq/") that I hope can give others more info on "quirks" and on using the uvc driver. 

Anyone knows **How do I record a video from the VLC media player?**

---

### Post by mörgæs on 2019-12-08
I suggest guvcview for recording video.

---

### Post by Holger_Gehrke on 2019-12-08
In vlc hit ctrl-r or select 'convert/save' from the 'Media'-Menu. Select the tab 'Capture Device' in the dialog, set the video device (and possibly the audio device) to use, then hit the button 'Convert/Save'. In the next dialog select 'Convert' and choose a profile (basically a collection of settings for container and codecs) or create a new one, then set the name for the destination file and hit Start. Hint: unless you select 'Display the output' you will not be shown what gets recorded while recording. Even if you do set this, the frame rate of the 'preview' will be very low, depending on the load generated by the selected profile. Hit the 'stop' button to finish recording.

Holger

---

