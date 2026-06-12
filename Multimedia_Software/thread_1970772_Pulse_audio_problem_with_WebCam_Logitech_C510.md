---
title: "Pulse audio problem with WebCam Logitech C510"
date: 2012-05-01
forum: Multimedia Software
---

### Post by fpoisson on 2012-05-01
Hello,

I've just installed the 12.04 and i see a difference between my USB bootable device used to install 12.04 and my current 12.04. 

The problem is on pulseaudio input device Logitech Webcam C510. When i'm testing it with the USB bootable device of 12.04 inside my "Sound setting > Input", it detect a "HD Webcam C510". Which is the real name of my webcam. Now after installation the "Sound setting > input" show me "081d" which correspond with to the id of the product. I try to force a new device.product.name properties inside default.pa (~/.pulse/default.pa) with no success.

I made a diff between during USB boot and now with command pacmd list-sources, here is the command "diff pacmd.txt pacmd_list_sources.12.04.txt", see file diff.txt.

Do you know how to restore this properties like during USB boot ?

Note that my webcam runs correctly on both video and sound :).

Thanks in advance for your suggestions,

---

