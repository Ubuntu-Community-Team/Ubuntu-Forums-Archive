---
title: "XAWTV: NVIDIA driver with 'nodga' flag not working"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by arsnova on 2007-07-18
I'm running Feisty ( 2.6.20-16-lowlatency) with the recent NVIDIA driver, and I'm unable to start XAWTV, even with the -nodga flag. Here's the output:

[INDENT]root@Caravaggio:/home/arsnova/Desktop/gspcav1-20070508# xawtv -nodga -device /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-lowlatency)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
[/INDENT]

Could anybody suggest a solution? I'm all Googled out.

Also, I'm trying to set up a webcam--I don't fully know how to interpret the results I'm getting, but I'm under the impression that the device simply isn't supported (one of those little obscure GP830 models, I think from Shenzhen.) Could anybody confirm this? Here's a bit of information:

output of xawtv -hwscan
[INDENT]This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-lowlatency)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter[/INDENT]

partial output of lsusb -v:
[INDENT]Bus 005 Device 019: ID 6000:0001  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x6000 
  idProduct          0x0001 
  bcdDevice            0.01
  iManufacturer          16 Trident
  iProduct               32 TVBOX[/INDENT]

I compiled and installed gspcav1-20070508, and ran 'modprobe gspca'. My dmesg output is:
[INDENT]
[ 6544.786000] usb 5-7: new high speed USB device using ehci_hcd and address 19
[ 6544.910000] usb 5-7: configuration #1 chosen from 1 choice
[ 7324.192000] Linux video capture interface: v2.00
[ 7324.195000] usbcore: registered new interface driver gspca
[ 7324.196000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered[/INDENT]

Ultimately, nothing exists in /dev/video0/

Sorry for the lengthy post, but thanks in advance to anyone who can advise me!

---

### Post by dabl on 2007-07-18
Yep, I have the exact same problem.  All indications are my PVR-150 is installed and set up correctly, ivtv-tune works, scantv shows it, xawtv -hwscan shows it, but when I try to run ```
xawtv -nodga -device /dev/video0
```, it's "NO JOY" 

same error as you have


  :confused:

---

