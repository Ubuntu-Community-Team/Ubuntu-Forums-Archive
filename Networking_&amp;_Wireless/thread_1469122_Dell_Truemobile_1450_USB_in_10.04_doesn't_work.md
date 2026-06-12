---
title: "Dell Truemobile 1450 USB in 10.04 doesn't work"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by curdog on 2010-05-01
[B]EDIT #2:  Problem solved in similar thread ([http://ubuntuforums.org/showthread.php?p=9228509#post9228509]("http://ubuntuforums.org/showthread.php?p=9228509#post9228509"))
See alexcuevo's posts.[/B]



EDIT:  Mods, looks like someone else read my mind & posted the same problem right before I did.  Please feel free to merge or whatever.
[http://ubuntuforums.org/showthread.php?t=1469109]("http://ubuntuforums.org/showthread.php?t=1469109")


I just did a clean install of 10.04 (32-bit), and my Dell Truemobile 1450 USB wireless adapter (broadcom?) is not recognized by the network manager (finds no networks)  However, it worked perfectly out of the box in 9.10.  I've looked through the 9.10 broadcom guide but no luck ([http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699"))

What I've done:

- reinstalled the "bcmwl-kernel-source" package in synaptic, but no luck.

- "lsusb" identifies the card correctly (but am not sure how to find the firmware version as it was not listed here)

Running from my 9.10 live CD, nm-tool reports (if this helps at all):
```
  Type:              802.11 WiFi
  Driver:            p54usb
  State:             connected
  Default:           yes
  HW Address:        00:90:4B:FA:B1:4B

```

I'm fairly new to ubuntu, but haven't found anything that's worked in the guides.  Any ideas?

---

