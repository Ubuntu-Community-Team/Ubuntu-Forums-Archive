---
title: "ADDON NWU275 Wireless Card. How To Install?"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by dHall81 on 2010-09-14
Hi, I have a wireless card that (apparently) came with a linux driver. It's a usb card and I've already plugged it in to the computer. At present it doesn't work, I've browsed the cd that came with it and there's a directory called linux that contains a folder with a "make" file in it but how do I install from a make file?

Sorry if I've missed anything important, I'm a total linux newb. Just ask and I'll get back to you. And thanks for any help in advance, I'm totally lost without the internet lol

---

### Post by blakep2 on 2010-09-15
Try going to System > Administration > Hardware Drivers.     See if it is listed here.

---

### Post by dineshs on 2010-09-15
Pl post the results of
```
sudo lshw -C network
```and```
iwconfig
```when the device is plugged in
> I've browsed the cd that came with it and there's a directory called linux that contains a folder with a "make" file in it but how do I install from a make file?I think you need to install [COLOR="SeaGreen"]build-essential[/COLOR] and then compile from source (There will be a file readme.txt that explains how to do it)

---

