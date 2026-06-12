---
title: "What is wrong with pulseaudio?"
date: 2012-03-23
forum: Multimedia Software
---

### Post by shenra on 2012-03-23
I was using my logitech usb headset just fine earlier today with it being easily detected and I was able to change to it for hearing my musing and chatting online.
However I have had this problem before with Ubuntu in which PulseAudio would not let me switch to the USB headset even when dmesg showed it being connected...

[26502.443876] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.3/input/input15
[26502.444065] generic-usb 0003:046D:0A0C.0006: input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.0-1.3/input3

And it would only let me use the on board mic and speakers.  So what I did was open system monitor and kill the pulse audio process and restarted it.  Viola yes I could now use my headset but now Ubuntu only sees it as analog.  I can live with this fix temporarily though.

:guitar:

Using Ubuntu 11.10, 64 bit.

---

