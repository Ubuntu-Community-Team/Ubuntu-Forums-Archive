---
title: "NetGear WNDA3100(v2) USB WiFi Drivers?"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by Cam! on 2012-11-23
I had to get a USB WiFi adapter due to a new router, and it won't work on my 64-bit 12.10 installation.

I know that I have to get the drivers from within Windows and do something with "ndiswrappers", but I'm not sure the exact method.

---

### Post by chili555 on 2012-11-23
Getting it to work in 64-bit is tricky. It may never work. However, if you are ready to try, hook up the ethernet temporarily and open a terminal and do:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
```Then run and post here:```
lsusb
```I have the Windows files but first we should verify your exact device.

Good luck to us both!

---

