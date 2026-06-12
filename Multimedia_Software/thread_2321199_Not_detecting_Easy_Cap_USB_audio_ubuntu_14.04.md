---
title: "Not detecting Easy Cap USB audio ubuntu 14.04"
date: 2016-04-21
forum: Multimedia Software
---

### Post by jagspaul on 2016-04-21
My ubuntu 14.0l LTS detecting Easy CAP and loading video driver (/dev/video0) but not detecting Easy CAP USB audio and no USB audio found.
VLC can play mt TV without audio.

arecord -l showing only mother board audio.

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC662 rev1 Alt Analog [ALC662 rev1 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

However when I plug any usb audio sound card the same is detecting properly. Only issue with Easy CAP USB audio.
 
My easy cap version  usbtv007

dmesg
==========

[ 4461.482226] usb 1-5: New USB device found, idVendor=1b71, idProduct=3002
[ 4461.482230] usb 1-5: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[ 4461.482234] usb 1-5: Product: usbtv007
[ 4461.482237] usb 1-5: Manufacturer: fushicai
[ 4461.482240] usb 1-5: SerialNumber: 300000000002
[ 4461.483096] usbtv 1-5:1.0: Fushicai USBTV007 Video Grabber


lsmod | grep usbtv
=====================
usbtv                  13511  0 
v4l2_common            15132  1 usbtv
videobuf2_vmalloc      13048  1 usbtv
videobuf2_core         39258  1 usbtv
videodev              108503  3 usbtv,v4l2_common,videobuf2_core


Can any body help me in this regards??

/jags

---

