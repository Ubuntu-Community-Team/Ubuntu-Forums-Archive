---
title: "webcam using V4L no image control..."
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by el-sio on 2007-07-19
Hello, I have a tiny webcam issue here...

The built in webcam of my computer (sony vaio type L mediacenter) is somehow recognized by ubuntu.
I installed easycam and it configured the driver automatically and I installed both camstream and camorama.
Hurray I can see my ugly face on the screen ! I can even take snapshots from it
However, I have a series of wierd problems :

When using camorama, Ican't have bigger image than 320x240 (the program crahses if Itry) and the quality isn't very good (image is kinda noisy...). Also the video settings buttons are not working and I can't change anything (brightness contrast...)
When using Camstream I can have maximum size image (640x480) but the quality isn't better and the control buttons (brightness...) don't work either.
When trying Egika, I have an ugly image where all the colors are inverted (like negative film) and I can't change anything with the control buttons...

I suppose my camera is using the V4L driver since it is listed as a "v4l device" in my hardware profile, and I wondered if I couldn't get better images and control using the V4L2 drivers, but Ihave no clue about how to do that, and when I ask Egika to use my webcam with V4L2 it says that it cannot open the device
Any help would be greatly appreciated !

Here is the very few info I could get about this webcam (it doesn't appear in LSPCI but it is listed in the "hardware information" list of the gnome control pannel, and I have a line about it in dmesg...)

```


el-sio@moria:~$ lsmod | grep video
video                  16388  0 
videodev               28160  2 gspca
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
el-sio@moria:~$ lsmod | grep gspca
gspca                 607824  1 
videodev               28160  2 gspca
usbcore               134280  8 gspca,xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

el-sio@moria:~$ dmesg | grep camera
[   21.500000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 

```

Vendor Vimicro Corp.

Actually, when I see the output of lsmod 'while using my webcam in camorama), I can see that the module used is gspca... Is this the module I have to tune to get my omage control working ?

BTW, how come skype doesn't include webcam support when Egika can ?

---

