---
title: "Sweex lw313"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by vince_fire on 2009-12-17
Hi there,

I've been trying for two days to get this Sweex lw313 (usb adapter, RT2770 + RT2720 chipset) to work, but it just won't budge! Anyone out there willing to help me out?

So, out of the box, it doesn't work. lsusb outputs the device as:
```

Bus 001 Device 002: ID 177f:0313

```So it doesn't recognize the device, am I right?

ifconfig does not list the device. I've tried installing the official Ralink drivers RT2870USB and RT3070USB, but both do not make any difference. I then tried to use ndiswrapper in combination with the drivers Supplied by Sweex. The driver installs fine and ndiswrapper -l outputs:
```

lw3x3_7x86 : driver installed
              device (177F:0313) present (alternate driver: rt2800usb)

```but the device still doesn't get recognized in lsusb. I then blacklisted the rt2800usb module, but to no avail...

I'm a Linux noob, and am out of ideas here... anyone willing to help me out?

---

