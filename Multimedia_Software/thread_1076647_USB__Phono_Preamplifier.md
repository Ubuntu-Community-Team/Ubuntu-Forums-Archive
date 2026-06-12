---
title: "USB  Phono Preamplifier"
date: 2009-02-21
forum: Multimedia Software
---

### Post by itlarson on 2009-02-21
I still have a large number of LP records, and am interested in digitising them.  For best quality I would like to bypass the soundcard, and so I am looking at USB preamps, the ART USB Phono Plus V2 in particular:

[http://www.artproaudio.com/products.asp?type=86&cat=9&id=128](http://www.artproaudio.com/products.asp?type=86&cat=9&id=128)

The only info I have been able to find is this:

[http://www.qbik.ch/usb/devices/showdev.php?id=4461](http://www.qbik.ch/usb/devices/showdev.php?id=4461)

Which seems to indicate that it is usable with alsa's snd-usb-audio module.  Does anyone have any thoughts as to if this will be difficult to get working?

---

### Post by markbuntu on 2009-02-21
That looks like a pretty cool device. How much does it cost?
Which kubuntu are you using?

---

### Post by itlarson on 2009-02-22
It's available for about 90$ from various sources.  Just check Google product search for "ART USB Phono Plus V2".  
   If anyone out there has experience with USB sound devices and the alsa snd-usb-audio module please tell me about it.

---

### Post by markbuntu on 2009-02-22
You should not have any problems with it for what you want to do since it is listed as supported by the alsa snd-usb-audio module. The driver may or may not provide all the functionality available but should basically work.

I asked which kubuntu you are using because setting it up with KDE4 is different that with KDE3 since KDE4 uses Phonon for sound services and KDE3 uses aRts.

---

