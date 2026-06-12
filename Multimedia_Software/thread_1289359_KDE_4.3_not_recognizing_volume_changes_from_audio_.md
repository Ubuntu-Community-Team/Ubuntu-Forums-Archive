---
title: "KDE 4.3 not recognizing volume changes from audio output devices"
date: 2009-10-12
forum: Multimedia Software
---

### Post by Lars Noodén on 2009-10-12
There are buttons on these two Logitech devices to increase or decrease the volume.  Pressing the buttons gets a response on the screen from KDE but no actual change in volume.  The meter can be decreased to 0% and it's still just as loud (or quiet) as at 100%.

```
[22734.360061] usb 3-1: new full speed USB device using uhci_hcd and address 5
[22734.617266] usb 3-1: configuration #1 chosen from 1 choice
[22734.709161] input: Logitech Logitech USB Speaker as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.2/input/input15
[22734.709320] generic-usb 0003:046D:0A04.0009: input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Speaker] on usb-0000:00:1d.1-1/input2

```

```
[22746.484019] usb 3-1: new full speed USB device using uhci_hcd and address 6
[22746.746351] usb 3-1: configuration #1 chosen from 1 choice
[22746.839613] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.3/input/input16
[22746.839714] generic-usb 0003:046D:0A0C.000A: input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.1-1/input3

```

---

