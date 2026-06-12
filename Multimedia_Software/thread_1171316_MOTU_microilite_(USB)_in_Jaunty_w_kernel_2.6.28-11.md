---
title: "MOTU microilite (USB) in Jaunty w/ kernel 2.6.28-11"
date: 2009-05-27
forum: Multimedia Software
---

### Post by aidan.dixon on 2009-05-27
Hi

Has anybody got a Motu Midi lite (5x midi in and out, fastlane) to work on Linux?

This USB device has vendor ID 0x7fd and product ID 0x1, which matches a device listed in linux-2.6.28/sound/usb/usbmidi.c (see static array snd_usbmidi_port_info[]) but as far as I can tell (well, there is no evidence in /proc/asound or dmesg) this device is not being recognised.

My Steinberg MI4 is recognised although, again, it's not obvious that its midi port is supported.

Anybody know how to get a list of MIDI ports out of ALSA by looking in /proc?  I guess if the /proc/asound/card.../midi* exists then that's it?

Regards,
Aidan

---

### Post by aidan.dixon on 2009-06-19
For those who don't already know, this device is not supported at all.  The alsa-users list got me the answer: although my device has the same USB vendor/device ID, it's not a fastlane midi device; apparently MOTU have used the same device ID for mulitple deivces (idiots!).

As documented elsewhere, MOTU have total disinterest in supporting the Linux community.

---

