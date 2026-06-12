---
title: "3G usb modems with card reader lost reader in modem mode"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by shtripok on 2009-09-15
I have 3G usb modem Huawei E1750. As many of 3G usb modems, it have MicroSD card reader. As many of 3G usb modems, it act as card reader and CD ROM device with windows drivers on first insertion.

Before act as modem, this gadget should obtain a magic command from the driver (under windows), or using usb_modeswich (under Linux). And then it swich into "modem mode", and add tty device to system.

The problem is: in Linux after switching into modem mode it lost both of storage devices. It can be not bad for cdrom with windows drivers, but bad for card reader. In Windows both storages stay accessible during modem connection.

I google it for a time, and see, that a lot of people have this problem, with many different modems from different manufacturers.

Is there a general way to use a full functionality of 3G modems with card readers - as modems and card readers simultaneously? As with Windows?

program used to enable modem mode for devices as described above:
[http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)

---

