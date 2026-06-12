---
title: "Modprobe &amp; Ndiswrapper lost on Re-Boot"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by NE Key on 2009-07-13
Using eeebuntu (Jaunty 9.04 on an Asus eeePC 900 A)kernel 2.6.29-1-netbook

Set up ndiswrapper with the net5211.inf driver.

Works fine - but it needs to be re-set on every re-boot; I use the terminal command sudo modprobe ndiswrapper and it works fine, until the next boot.

I have done modprobe ndiswrapper -m but it does not keep after re-boot.

I think my current kernel demands that etc/modprobe.d/ndiswrapper is renamed ndiswrapper.conf - which I have done.


How do I store these ndiswrapper settings so they are not lost on re-boot ?

---

