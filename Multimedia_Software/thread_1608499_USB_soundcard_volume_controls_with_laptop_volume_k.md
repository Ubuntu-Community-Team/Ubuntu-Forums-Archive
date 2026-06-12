---
title: "USB soundcard volume controls with laptop volume keys"
date: 2010-10-29
forum: Multimedia Software
---

### Post by tristan on 2010-10-29
Gday all

I've got my xubuntu 10.10 install just about perfect on a little acer aspire d250, apart from a small sound useability issue:
 
In the interests of simplicity and resource usage I removed pulseaudio. After a bit of fiddling I got it so that my USB soundcard (ProDac) is recognized and automatically set as the default soundcard when plugged in. Any sound applications automatically use the USB sound if it present, no need to **** around with pulse. The only problem is that my netbook's volume control keys still only control the master volume of the inbuilt soundcard, and have no effect on the usb sound.

Does anyone know of a way to change which sound device these keys actually effect? I'd ideally like to write a little script so that when the usb device is detected the keys are remapped.

Any help appreciated.

---

### Post by newyorkcityjay on 2011-09-14
I am running into a similar issue.  I am running Xubuntu Oneiric Beta with Pulse.  I can make my USB sound card work just fine with padevchooser, but my laptop volume keys still only want to work with the onboard sound, although they controlled the USB when I was still running Ubuntu Natty.  I can't tell what the next, previous, play/pause buttons are doing, if anything.

---

