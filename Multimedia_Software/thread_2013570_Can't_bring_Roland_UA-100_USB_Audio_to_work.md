---
title: "Can't bring Roland UA-100 USB Audio to work"
date: 2012-07-01
forum: Multimedia Software
---

### Post by Karl Achs on 2012-07-01
Hi all,

I'm trying desperately to bring my Roland UA-100 to work. In the attachment is the output of alsa-info.sh. I deleted parts regarding my internal sound card, which is working.

The segfaults in the syslog are caused by a not correct example code for alsa, which I downloaded and not part of the problem.

The "usb_set_interface failed" appears every time when I try aplay/arecord.

When I plug out and plug in the UA-100 following appears in the syslog:

```
Jul 1 09:51:48 DrOS kernel: 3:0:1: usb_set_interface failed
Jul 1 09:51:50 DrOS kernel: usb 5-2: USB disconnect, device number 3
Jul 1 09:51:56 DrOS kernel: usb 5-2: new full-speed USB device number 4 using xhci_hcd
Jul 1 09:51:56 DrOS mtp-probe: checking bus 5, device 4: "/sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/usb5/5-2"
Jul 1 09:51:56 DrOS mtp-probe: bus: 5, device: 4 was not an MTP device
Jul 1 09:51:58 DrOS kernel: 4:0:1: usb_set_interface failed
```Isn't xhci USB 3.0? Due to the age of the UA-100 I assume it's a USB 1.0/1.1 device.

Thanks and regards
K

---

