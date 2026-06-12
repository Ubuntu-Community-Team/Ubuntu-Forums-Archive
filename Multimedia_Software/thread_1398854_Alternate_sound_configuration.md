---
title: "Alternate sound configuration"
date: 2010-02-05
forum: Multimedia Software
---

### Post by NJ0E on 2010-02-05
Hell all,

I have a unique situation here.  I have a Dell Inspirion 5150.  The onboard sound card was blown 3 years ago.  OS is Ubuntu 8.10.  I am also a HAM radio operator and use the computer for digital modes using a USB device that acts as an external sound card modem for me.  

The program that I use for that is fldigi.  
The device is Signalink USB by Tigertronics.  the device has the ability to have speakers plugged in to it.
Question:  Is there a way to have the computer send the audio out the USB cable to the device?  

I have looked at my sound settings and there are USB devices but none of them are the one(s) that I use with my Signalink device.

If it can't be done, no worries -- have not really needed it so far.  Just something nice to have.

Thanks for the help!

---

### Post by VertexPusher on 2010-02-05
> **NJ0E said:**
> Is there a way to have the computer send the audio out the USB cable to the device?
Yes, if the device is a USB class-compliant audio device. If it is, the system will recognize it automatically and load an ALSA driver for it. It will appear in the list of playback devices that you see when you enter
```
aplay -l
```
in a terminal window.

---

### Post by NJ0E on 2010-02-07
Thanks, I'll take a look when I get the chance!

---

