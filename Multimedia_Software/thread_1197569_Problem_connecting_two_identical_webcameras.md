---
title: "Problem connecting two identical webcameras"
date: 2009-06-26
forum: Multimedia Software
---

### Post by josteinaj on 2009-06-26
I'm trying to connect two Logitech QuickCam Messenger cameras to my computer. They are both discovered and [FONT="Courier New"]lsusb[/FONT] displays them like this:

[FONT="Courier New"]Bus 001 Device 015: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 014: ID 046d:08f0 Logitech, Inc. QuickCam Messenger[/FONT]

Detailed output of the cameras using [FONT="Courier New"]lsusb -v[/FONT]: [ATTACH]119022[/ATTACH]

My problem is that it's just the first camera I connect that are installed as a working camera in Ubuntu. I never get a [FONT="Courier New"]/dev/video1[/FONT] or similar, just the one [FONT="Courier New"]/dev/video0[/FONT].

I'm running Ubuntu 9.04 x64, however the same thing happens on my laptop running Ubuntu 8.10. The laptop (Acer Aspire One) has a built-in webcam. The built-in webcam and the first of the two QuickCams that are connected works properly, so it seems the problem is with Ubuntu itself and not my specific configuration.

Connecting the cameras in sequence and checking [FONT="Courier New"]dmesg[/FONT], I get:

[FONT="Courier New"][142318.752022] usb 1-4: new full speed USB device using ohci_hcd and address 6
[142318.971916] usb 1-4: configuration #1 chosen from 1 choice
[142319.121668] videodev: "QCM USB Camera" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[142319.121673] usbvideo: QCM on /dev/video0: canvas=320x240 videosize=320x240
[142319.122984] input: QCM button as /devices/pci0000:00/0000:00:0a.0/usb1/1-4/input/input8
[142319.620853] usbvideo: Packet Statistics: Total=32. Empty=0. Usage=100%
[142319.620858] usbvideo: Transfer Statistics: Transferred=0 B Usage=0%
[142328.510147] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[142329.068020] usb 1-1: new full speed USB device using ohci_hcd and address 7
[142329.287685] usb 1-1: configuration #1 chosen from 1 choice
[142329.297025] usbvideo: IBM USB camera driver: Too many devices!
[142329.297186] QCM: probe of 1-1:1.0 failed with error -12[/FONT]

What can i do to get both cameras working?

---

