---
title: "Sound not seeing Zoom H4 usb mic"
date: 2013-06-22
forum: Multimedia Software
---

### Post by ktat on 2013-06-22
Hi, I'm using Ubuntu 12 LTS.  I was wanting to use skype the other day and so I plugged in my Zoom H4 to use as a mic.  When I opened up the sound settings in ubuntu to select it as the input it was only listed as an output device.  This is a bit strange as it is only an input device - it has no speakers.

The other strange thing is that when I started up audacity to see if it was working there it was fine.  In audacity I have the host set to alsa, playback is set to pulse and recording to H4: USB Audio (hw:2,0): Front Mic:1.  Skype doesn't let me select anything other than pulseaudio server (local) for the mic option.

I assume that pulseaudio is the problem here.

```
the output for lsusb is:

Bus 001 Device 002: ID 046d:080f Logitech, Inc. Webcam C120
Bus 001 Device 006: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 1686:0045 ZOOM Corporation H4 Digital Recorder
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

If someone can help - I really just need to be able to use my usb mic while using skype.
Thanks.

---

### Post by ktat on 2013-06-28
some help with this would be really useful - even if just to show me where to log a bug... ta.

---

