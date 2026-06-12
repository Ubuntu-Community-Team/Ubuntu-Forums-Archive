---
title: "Creative Bluetooth Audio D1"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by steelerguy631 on 2010-12-19
I have the Creative S2 Inspire 2.1 speakers.  It came with the Creative Bluetooth Audio D1 USB transmitter. This is not working with Ubuntu.

The kernel recognizes the device when plugged in (although I do get the endpoint lacks sample rate error):
[ 2008.671749] generic-usb 0003:041E:0005.0008: hidraw0: USB HID v1.11 Device [Creative Bluetooth Audio D1] on usb-0000:00:1a.0-1.1/input2
[ 2008.717765] 11:1:1: endpoint lacks sample rate attribute bit, cannot set.

The bluetooth manager sees the device and says it is set up.  Bluetooth preferences shows it as being set up.  I do not see anything special in alsamixer.  My laptop (HP Envy 17) internal speakers work, the HDMI speakers on my HDMI connected monitor work, but no sound from my speakers.

Any idea what I need to do to get these working?

---

### Post by bailey86 on 2011-03-18
Did you manage to get this device to work with Ubuntu?

---

