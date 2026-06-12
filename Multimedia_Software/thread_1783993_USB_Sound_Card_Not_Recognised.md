---
title: "USB Sound Card Not Recognised"
date: 2011-06-16
forum: Multimedia Software
---

### Post by K-JC on 2011-06-16
Hi,

I've recently put Ubuntu 11.04 onto an unused server with the plan of converting it into just a standard desktop PC, however it was lacking some of the basic components. After a struggle I managed to get an old Nvidia graphics card to work nicely and I bought a £2 USB sound card from ebay and I've had no luck whatsoever in even getting it recognised.
When plugged into windows the information given about the device is 'Generic USB Audio'
I've restarted after each time I've tried to fix the issue and I've been mucking around a bit with ALSA following instructions from every forum post I could find but with no success.

I'll be grateful for any help and if there's anything you need to me to do to help diagnose the problem just let me know! Below is the link to some diagnostic I ran.

[http://www.alsa-project.org/db/?f=135ab6f5fa5cf5114926d4cfa69f0a81a182bab1](http://www.alsa-project.org/db/?f=135ab6f5fa5cf5114926d4cfa69f0a81a182bab1)

Cheers!

---

### Post by lidex on 2011-06-18
Have you checked to see if that card is supported by alsa? Alsa is not seeing it, how about your system? What is this output:
```
lsusb
```

---

### Post by K-JC on 2011-06-18
Hi,  lsusb returns:

```
Bus 002 Device 014: ID 1130:f211 Tenx Technology, Inc. TP6911 Audio Headset 
Bus 002 Device 008: ID 0000:0000    
Bus 002 Device 007: ID 0461:0010 Primax Electronics, Ltd  
Bus 002 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` I've had a quick look around now I know the manufacturer but still not had much luck. I'll keep at it but any other help would be appreciated.

Edit:

After a bit more looking [http://www.linuxquestions.org/questions/linux-software-2/usb-speakers-as-default-649705/#post3186541](http://www.linuxquestions.org/questions/linux-software-2/usb-speakers-as-default-649705/#post3186541) solved the problem! The soundcard shows up and it works but only with headphones. I tried plugging in the speakers built into my laptop but it just crackles then the computer drops the soundcard.

I think I'll just try and buy an internal soundcard.

---

