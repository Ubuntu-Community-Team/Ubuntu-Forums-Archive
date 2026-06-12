---
title: "Unable to install maverick because of bluetooth"
date: 2010-08-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NHclimber on 2010-08-19
Not sure which package to file this bug under so it's not in Launchpad yet.

I just tried to install Alpha-3 using the cd iso (kubuntu image), but the mouse cursor won't move and the keyboard won't accept input.

I believe it's because /lib/udev/rules.d/70-hid2hci.rules runs hid2hci on my bt mini-receiver. I had to fix this in lucid after a recent upgrade from karmic [by commenting out hid2hci.rules].

Output from lsusb
```
Bus 005 Device 004: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 005 Device 003: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 005 Device 002: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)

```

~Peter

---

