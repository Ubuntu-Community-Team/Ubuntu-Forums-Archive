---
title: "logitech quickcam express problem"
date: 2009-05-26
forum: Multimedia Software
---

### Post by monkeyslayer56 on 2009-05-26
im on ubuntu 9.04  and have a logitech quickcam express but it wont work in cheeses or anyother viewer i try. i have found some drivers for it but when compiling i get this error ```
make[2]: *** [/home/josh/.local/share/Trash/files/qc-usb-0.6.4/qc-driver.o] Error 1
make[1]: *** [_module_/home/josh/.local/share/Trash/files/qc-usb-0.6.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [quickcam.ko] Error 2
ls: cannot access quickcam.ko: No such file or directory
[!] Looks like the driver compilation failed.
```
i really am lost because i get similary errors on almost everything i try to compile i do have the build essentals package installed
if there is a better way to get this working im am open to suggestions/constructive criticism

---

### Post by subslug on 2009-05-26
Try plugging the camera in and running 'modprobe quickcam'  then see what happens in cheese.

---

### Post by monkeyslayer56 on 2009-05-26
still "camera not found" anyother ideas? and since i ahve problems getting anything to compile corectly should i try moveing this to another section?


UPDATE: it works in camorama but nothing else

---

### Post by subslug on 2009-05-27
Well I'm fairly sure the quickcam modules are already loaded or else camorama wouldn't work so it sounds like a software issue with cheese of some kind.

I don't suppose if you start cheese from a command line it gives you anymore details...?

Judging from the number of posts about quickcam cameras there seems to be a common theme with 9.04 going on.
On my Dell netbook the built in camera is working with cheese and 9.04 so it looks like a Logitech deal of some sort.
No doubt someone will find a work around soon.

---

### Post by monkeyslayer56 on 2009-05-27
well im not makeing much progress and ive about search all of google but hopefully like u said there will be a work around soon
when i loauch cheese from terminal i get

```
josh@josh-desktop:~$ cheese

(cheese:9336): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

```
if nothing else i don't really care if cheese picks it up i was just using that for testing it what i really want is for skype to pick it up (witch it doesn't)
does this mean all i can do is wait?

---

### Post by Daveski on 2009-05-29
> **subslug said:**
> Judging from the number of posts about quickcam cameras there seems to be a common theme with 9.04 going on.

These QuickCams also cause BSOD on Windows XP and Vista with the newest drivers. The 'solution' is to install old drivers and constantly prevent Windows from updating them...

---

