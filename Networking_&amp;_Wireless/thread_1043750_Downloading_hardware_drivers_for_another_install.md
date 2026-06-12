---
title: "Downloading hardware drivers for another install?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by midtown on 2009-01-18
Hello!

I have a broadcom 43xx card in this laptop, and just installed Jaunty. The wireless doesn't work out of the box, but the only internet access I have is wireless, so is there a way for me to download the jaunty package (Broadcom STA wireless drivers) in Intrepid (what I am using currently) for Jaunty and install and activate it in the jaunty partition offline?

Thanks for any tips!

---

### Post by x33a on 2009-01-18
if you have a deb or even a tarball, then you can transfer them to the other computer and install using dpkg or compiling from source.

---

### Post by midtown on 2009-01-18
> **x33a said:**
> if you have a deb or even a tarball, then you can transfer them to the other computer and install using dpkg or compiling from source.

Thanks, although I know how to do that. What I don't know is what package the proprietary Broadcom STA drivers are in or how to get the Jaunty ones in Intrepid, so I am stuck at getting the package in the first place. Any hints on finding that information out?

---

### Post by x33a on 2009-01-18
maybe this link could be helpful

[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

---

### Post by Ayuthia on 2009-01-18
Jaunty already has the Broadcom STA driver in System->Administration->Hardware Drivers.  You shouldn't have to download anything to make it work.  If you are having problems with it, try:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

