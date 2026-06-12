---
title: "Nvidia Blues -- How to Un-Ring the Bell?"
date: 2011-02-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bruc33ef on 2011-02-26
Please help -- apt-get update and upgrade got me to nvidia-current, It blacked out my screen and now I'm living in reduced-video rescue-mode hell.  I've read the Stickies, but there are no specifics on how to downgrade back to full video.  My Nvidia GeForce Go7300 card (Lenovo 3000N200 laptop) never worked completely right in Maverick or Natty since the nvidia-7300 driver.  Could someone walk me through the exact files I need to delete and install while I wait for Nvidia to get its act together?

Many thanks!

---

### Post by mc4man on 2011-02-26
get to terminal of any sort (recovery mode if need be 
```
sudo apt-get purge nvidia-current
```
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```
reboot
If desired then enable the mesa 3d drivers (libgl1-mesa-dri-experimental

---

### Post by bruc33ef on 2011-02-26
> **mc4man said:**
> get to terminal of any sort (recovery mode if need be 
```
sudo apt-get purge nvidia-current
```
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```
reboot
If desired then enable the mesa 3d drivers (libgl1-mesa-dri-experimental
Thanks, mc4man!  Worked great, even the mesa 3d drivers.  Much appreciated.

---

