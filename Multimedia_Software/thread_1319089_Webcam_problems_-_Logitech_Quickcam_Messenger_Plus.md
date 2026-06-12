---
title: "Webcam problems - Logitech Quickcam Messenger Plus"
date: 2009-11-08
forum: Multimedia Software
---

### Post by gontofe on 2009-11-08
I've been searching in vain for an answer to this, and keep falling on old instructions to install qc-usb drivers, but as, according to [https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams") 

"The webcam works automatically in 9.10 (the 2.6.30+ kernels) with the gspca_stv06xx driver"

I believe this webcam should work 'out of the box' as I have recently upgraded to Karmic.

However, when I plug it in, lsusb gives:

```
Bus 002 Device 011: ID 046d:08f6 Logitech, Inc. QuickCam Messenger Plus

```

Which seems to be a good start. When I check dmesg, I get 

```
[ 7134.520442] usb 2-1.6: new full speed USB device using ehci_hcd and address 11
[ 7134.615783] usb 2-1.6: configuration #1 chosen from 1 choice
[ 7134.617036] STV06xx: Probing for a stv06xx device
[ 7134.617042] gspca: probing 046d:08f6
[ 7134.617047] STV06xx: Configuring camera
[ 7134.617051] STV06xx: st6422 sensor detected
[ 7134.617055] STV06xx: Initializing camera
[ 7134.879772] gspca: probe ok
[ 7134.879901] STV06xx: Probing for a stv06xx device
[ 7134.879906] gspca: probing 046d:08f6

```

Which I believe to also be a good sign. However, when I try and launch cheese, I get the following:

```
mike@mike-laptop:~$ cheese -v
Cheese 2.28.1 
Probing devices with HAL...
Found device 046d:08f6, getting capabilities...
Detected v4l2 device: Camera
Driver: STV06xx, version: 132608
Capabilities: 0x05000001

Probing supported video formats...
libv4l2: error turning on stream: Input/output error

```

When I try and test the webcam using gstreamer-properties, I get the following:

```
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1886): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
system error: Input/output error]
```

What can I do to get this working?

---

### Post by Arup on 2009-11-08
It could be video for linux error and probably the drivers need the older v4l instead of v4l2. Try Camorama which is in the repos and is made for older video for Linux devices.

---

### Post by gontofe on 2009-11-08
Camorama gives: Unable to capture image

xawtv does show an image, although the contrast/brightness etc are awful!

This only works when the webcam is plugged in directly to my laptop, and not through the usb hub...

Any other output I can post to help?

---

### Post by macstevejb on 2009-11-08
Try opening Camorama using this command in the terminal:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camorama

regards :D

---

### Post by gontofe on 2009-11-08
That does work with camorama, but not with Cheese, which just shows the test pattern, or skype, which does the old green fuzzy thing...

---

### Post by Rhemat on 2009-11-08
I can see the video just fine in cheese, and I can take a photo, but when I try to record, I just get a still frame.  When I click to stop recording, Cheese just hangs.  I have to force quit to get Cheese to close, and the file it creates is 0 bytes, containing no video and audio.

---

### Post by gontofe on 2009-11-10
We aren't having the same issue then!

---

### Post by Maddog Battie on 2009-12-15
For those that are having problems with Skype and Logitech Quickcam Messenger Plus (like me) then the following command sorted me out:


LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &

---

### Post by timcredible on 2009-12-15
that sort of works - i get a grainy pic that's about 1/4 of the picture.  in my case i have a logitech quickpro 9000 which worked perfectly with my old computer, but not with my new computer.  i already know that my new computer must have a newer usb hardware because i had to manually load a module to get media card reader to work.  i wonder if there's something similar for the webcam.  output from lsusb:
```

Bus 007 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 007 Device 002: ID 046d:c50d Logitech, Inc. Cordless Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 03f0:5d11 Hewlett-Packard Photosmart C5200 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

