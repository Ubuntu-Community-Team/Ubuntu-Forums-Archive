---
title: "KDE doesn't recognize microphone on logitech headset; GNOME does..."
date: 2014-06-09
forum: Multimedia Software
---

### Post by reubenf on 2014-06-09
I have a Logitech Clearchat USB headset. When I plug it in in GNOME, the microphone is available in the options for sound sources. When I plug it in in KDE, the microphone is listed in the Phonon(?) UI, but is grayed out, and doesn't work. However, it is recognized as a playback device, and audio plays through the headset. If I go into alsamixer and turn up the volume on the microphone, it becomes available to KDE and works; but I have to do that every time. How do I make KDE automatically recognize and initialize the device?

In syslog, the following is logged after I plug it in:

Jun  9 11:55:26 fridge kernel: [315747.088122] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1/2-4.1:1.3/input/input28
Jun  9 11:55:26 fridge kernel: [315747.088259] hid-generic 0003:046D:0A0B.0012: input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:0b.0-4.1/input3
Jun  9 11:55:26 fridge mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4.1"
Jun  9 11:55:26 fridge mtp-probe: bus: 2, device: 13 was not an MTP device
Jun  9 11:55:26 fridge rtkit-daemon[4604]: Successfully made thread 8609 of process 4602 (n/a) owned by '1000' RT at priority 5.

lsusb shows:

Bus 002 Device 013: ID 046d:0a0b Logitech, Inc. ClearChat Pro USB

---

