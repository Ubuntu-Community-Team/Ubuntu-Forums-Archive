---
title: "DV Capture dropping frames"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by brousch on 2007-10-30
I just got a new Panasonic PV-GS80 MiniDV camcorder and am trying to capture the DV for editing in Kino. I am able to view the video smoothly on the camera's LCD and capture video over firewire, but it comes in at very poor quality. I am running Gutsy on a 2GHz proc and 512MB of RAM so I don't think insufficient resources are the problem. I am using firewire via a PCMCIA add-on card.

When I capture with dvgrab, I get a lot of the following messages:
"dvgrab-008.avi": buffer underrun near: timecode 00:01:45.07 date 2007.10.30 19:14:31
This error means that the frames could not be written fast enough.

This seems to indicate that my hard disk is too slow? It is a 160GB laptop drive less than 6 months old. 

There seemed to be problems with DMA not working for some hard disks back in Feisty, and I see that DMA is not turned on for /dev/sda1. It also seems to be impossible to turn DMA on. When I try sudo hdparm -d1 /dev/sda1 I get the error:
/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

I think I have all of the proper modules loaded for dv:
lsmod | grep 1394
video1394              19800  0 
dv1394                 20824  0 
raw1394                31096  0 
ohci1394               36528  2 video1394,dv1394
ieee1394               96312  4 video1394,dv1394,raw1394,ohci1394

I've reached the limits of my troubleshooting, so if anyone else has any ideas I'd love to hear them.

---

### Post by asmiller-ke6seh on 2007-11-21
I thought I remember reading, elsewhere, that if you have CompizFusion up and running during capture, that frames are dropped.

You might want to try turning off CompizFusion during capture and see if that resolves your symptoms. Let us know if that helps, please?

---

### Post by brousch on 2007-11-23
I did not have compiz running. However, I did buy a new IEEE1394 PCMCIA card, and video grab is working correctly now. It looks like the combo USB/Firewire card I was using was the problem.

---

