---
title: "PixelView PlayTV Box"
date: 2009-10-28
forum: Multimedia Software
---

### Post by fberbert on 2009-10-28
Hi folks,

I am using Karmic and got a PixelView to capture video. My issue is, when I attach the USB cable into the OS with the Box turned off, it is recognized, as follows:

Oct 28 20:15:14 zeus kernel: [23950.020038] usb 1-8: new high speed USB device using ehci_hcd and address 9
Oct 28 20:15:14 zeus kernel: [23950.161620] usb 1-8: configuration #1 chosen from 1 choice
Oct 28 20:15:14 zeus kernel: [23950.162993] em28xx: New device USB 2821 Video @ 480 Mbps (eb1a:2821, interface 0, class 0)
...
Oct 28 20:15:16 zeus kernel: [23952.104032] em28xx #0: v4l2 driver version 0.1.2
Oct 28 20:15:17 zeus kernel: [23953.085686] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0

And when I TURN ON the Box, it is deregistered:

Oct 28 20:18:58 zeus kernel: [24173.678228] usb 1-8: USB disconnect, address 10
Oct 28 20:18:58 zeus kernel: [24173.678307] em28xx #0: disconnecting em28xx #0 video
Oct 28 20:18:58 zeus kernel: [24173.678310] em28xx #0: V4L2 device /dev/vbi0 deregistered
Oct 28 20:18:58 zeus kernel: [24173.678363] em28xx #0: V4L2 device /dev/video0 deregistered
Oct 28 20:18:58 zeus kernel: [24173.678430] tuner-simple 6-0063: destroying instance

Does someone get the same problem? Or is it a possible hardware issue?

Thanks.

---

