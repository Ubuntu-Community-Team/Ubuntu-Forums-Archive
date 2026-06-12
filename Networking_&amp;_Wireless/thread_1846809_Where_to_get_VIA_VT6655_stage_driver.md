---
title: "Where to get VIA VT6655 stage driver?"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by abacabus on 2011-09-19
This is for Ubuntu 11.04:
According to linuxwireless.org, the driver for the wireless card VIA VT6655 should be in the driver/staging directory.
I found the source files for it, but when I searched for the driver using "modprobe -l | grep staging" I only found the driver for VT6656 (vt6656_stage.ko, notice different number), but not for the VT6655.
Actually, I found most staging drivers. It seems that only VT6655 is missing...
So, how do I get it? Or build it?

Thank you in advance.

---

### Post by praseodym on 2011-09-19
Hi,

imho this card doesnt work with a linux driver (too old, driver _and_ card, respectively), try ndiswrapper instead:
```
sudo apt-get install ndisgtk ndiswrapper-utils-1.9 ndiswrapper-common
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2886422/windows_driver_VIA_VT6655.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2886422/windows_driver_VIA_VT6655.tar.gz)
tar xvf windows_driver_VIA_VT6655.tar.gz
sudo ndiswrapper -i windows_driver_VIA_VT6655/VNWL.inf
ndiswrapper -l [COLOR="Red"]#check[/COLOR]
```
If the driver is shown, then load the module:

```
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```

---

### Post by abacabus on 2011-09-20
Thank you for your answer, highly relevant in most cases, but ndiswrapper is not an option for me. Therefore, the question remains:
Where is vt6655_stage.ko ?

---

### Post by praseodym on 2011-09-20
Check with:

```
modinfo vt6655_stage
locate vt6655_stage.ko
```

---

### Post by abacabus on 2011-09-21
Thank you again for the answer, but "modinfo vt6655_stage" reveals that the driver does not exist on the machine (as I indicated in the original question). So the question remains:
Where can I get vt6655_stage.ko? (or build it)

---

