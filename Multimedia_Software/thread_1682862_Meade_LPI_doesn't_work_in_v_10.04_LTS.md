---
title: "Meade LPI doesn't work in v 10.04 LTS"
date: 2011-02-06
forum: Multimedia Software
---

### Post by jch121 on 2011-02-06
I've loaded UBUNTU 10.04 LTS on a Dell Latitude D620. I'm now trying to get my Meade LPI webcam to work. I've loaded Autostar suite (works fine), loaded Kstars (works fine). I've installed v4l2 (no error messages), I've installed INDI (with this error msg -- 
(Reading database ... 161173 files and directories currently installed.)
Unpacking indi (from .../indi_5%3a0.5-0ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/indi_5%3a0.5-0ubuntu7_i386.deb (--unpack):
 trying to overwrite '/usr/bin/indiserver', which is also in package libindi0 0:0.6-0ubuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/indi_5%3a0.5-0ubuntu7_i386.deb

Kstars Devices/Device Manager does not report any devices in any category.  
The LPI worked fine in this PC under Windows. I've tried the LPI in all four USB ports, no difference, always this is the same message set...
[14078.941035] usb 4-2: new full speed USB device using uhci_hcd and address 3
[14079.102172] usb 4-2: configuration #1 chosen from 1 choice
[14079.107323] usb 4-2: SN9C10[12] PC Camera Controller detected (vid:pid 0x0C45:0x602A)
[14079.220068] usb 4-2: No supported image sensor detected for this bridge

I am not experienced enough in Linux to even know if these error messages are meaningful. I think it all means that the LPI is recognised as an LPI, but for some reason no application can see it. Not Cheese either, or Camorama....

Help?  and lots of thanks.

---

