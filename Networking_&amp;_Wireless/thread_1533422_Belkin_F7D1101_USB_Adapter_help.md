---
title: "Belkin F7D1101 USB Adapter help"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by MarioMaster100 on 2010-07-17
I'm trying to install the Belkin F7D1101 USB adapter on Ubuntu 10.04. I installed ndisgtk and located the file I needed and it says the driver is installed but the usb isn't showing up like in windows (I'm mostly a windows user and I don't know much about ubuntu). Since I'm new to Ubuntu step by step instructions would be helpful.

---

### Post by MarioMaster100 on 2010-07-18
I have googled this and I still don't know how to do it I have rebooted it and it says I have the driver installed but the USB adapter isn't turning on like it should after the driver is installed like on windows. Does anyone know how to do this?

---

### Post by MarioMaster100 on 2010-07-19
Would installing wifi radar help?

---

### Post by pwnjangles on 2010-08-05
I'm have the same problem I tried it with wifi radar but its pointless when the adapter doesnt come on to find signals and I don't know which is the right inf file to select when trying to install with ndis their all in xp/vista/wndows7 folders

---

### Post by flash63 on 2010-08-06
Hello,
checkout the USB-ID:
```
lsusb
```
it looks like this
```
Bus 001 Device 001: ID 050d:945a Belkin Components
```
Very probably it is a device with Realtek Chipset. The manufacturer provides appropriate drivers.

---

### Post by Linux_Youth******* on 2010-08-06
Check another forum post: [http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101)

The instructions listed in that post are what I used to install this same device on my Mepis 8.5 installation, which is based on Debian much like Ubuntu. It should work well for you. If not then well, at least I tried. Good luck!

---

