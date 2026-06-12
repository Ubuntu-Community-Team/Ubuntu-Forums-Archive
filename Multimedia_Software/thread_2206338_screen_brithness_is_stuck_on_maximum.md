---
title: "screen brithness is stuck on maximum"
date: 2014-02-18
forum: Multimedia Software
---

### Post by chillering on 2014-02-18
ubuntu 13.10 (64-bit freshly installed on Dell Inspiron N series)
Screen brightness is too bright. 
The function keys (F4 and F5) display brightness bar in upper right corner and it flickers when I press key to reduce it but it is like kinda stuck on maximum. 

Output of code;


for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

prints the attached output.

---

### Post by Toz on 2014-02-18
With root privileges, try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...and log out and back in again to test.

If it doesn't work, post back the results of:
```
lspci -k | grep -iA2 VGA
```
...and
```
uname -a
```

---

### Post by chillering on 2014-02-18
> **Toz said:**
> With root privileges, try creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...and log out and back in again to test.

If it doesn't work, post back the results of:
```
lspci -k | grep -iA2 VGA
```
...and
```
uname -a
```

I'm new to ubuntu. Please, mention some easy steps. This looks very complicated..

---

### Post by chillering on 2014-02-18
It worked. Problem solved :)

---

### Post by shaima2 on 2014-02-24
thank you very much.. problem solved successfuly
:p

---

