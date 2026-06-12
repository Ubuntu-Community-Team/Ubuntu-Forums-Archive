---
title: "How to change Screen Res"
date: 2009-12-13
forum: Multimedia Software
---

### Post by Me@karmic on 2009-12-13
Hi All, 
Need some help here. I am running Ubuntu 9.10 on my hp compaq nx6120 notebook. Problem is my screen res is max up to 1024x768(4:3). Is there anyway I can increase this. Anyhelp would be appreciated. ;)

------------------------ lshw -C Display -------------------------
system@sys-karmic:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0400000-d047ffff ioport:7000(size=8) memory:c0000000-cfffffff(prefetchable) memory:d0480000-d04bffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d0500000-d057ffff
system@sys-karmic:~$

---

### Post by deathbyswiftwind on 2009-12-13
Ive been wondering the same thing. Ive tried messing with xorg files but to no avail. Im thinking it must need a driver to support the higher resolution but I myself have not been able to find one after hours of googling.

---

### Post by Me@karmic on 2009-12-13
Well.. on Karmic I believe there is no xorg.conf file to edit. 

Tried to load the Startup-manager, but it does not help.

---

### Post by jmate24 on 2009-12-13
have you looked at the intel graphics how to?
i had to use it with mine to get the nice graphics. the safe way works the best but if you are using nvidia then go to system>administration>hardware drivers and see if you have the necessary drivers for your machine.

jmate24--:D

---

### Post by Me@karmic on 2009-12-13
**[COLOR=DarkRed][/COLOR]**Tied this as well:
**sudo xrandr -s 1280x800**
**sudo xrandr -q**
and finally tried the following command:
gksudo displayconfig-gtk 

The last even does not run and terminated without any error.

---

