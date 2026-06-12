---
title: "SYBA USB audio stopped working on Ubuntu lucid"
date: 2011-05-10
forum: Multimedia Software
---

### Post by wagaboy on 2011-05-10
hi,

I have a broken audio port on my laptop, so I've been using Syba audio USB.([http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_2?s=electronics&ie=UTF8&qid=1305077238&sr=1-2](http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/ref=sr_1_2?s=electronics&ie=UTF8&qid=1305077238&sr=1-2))

It was working fine till today--sound used to switch from laptop speakers to usb device. The volume control slider on the desktop panel does not switch to Usb device automatically, so I manually got to Sound Preferences -> Output and select the USB device.

**PROBLEM:**
But today, when I tried to select the USB device as described above, the sliders in the "Output" tab went crazy, and I don't get any sound from the USB device. 

Here's a couple of things that I tried:
1. Reboot-- didn't help.
2. Check if USB is working on another system-- works fine.

---

### Post by lidex on 2011-05-11
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

