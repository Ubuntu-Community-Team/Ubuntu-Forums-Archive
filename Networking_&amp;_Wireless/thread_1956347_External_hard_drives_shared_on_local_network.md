---
title: "External hard drives shared on local network"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by getphuture on 2012-04-10
Good day all,

I restored my old Apple PowerBook G4 ( Power PC ) and switch from XFCE to LXDE :-).
It's a Ubuntu Lucicd 10.04.4 LTS 
I would like to use it to store data too. Basically it's a notebook with 2 external hard drives plugged:
* 1 is a 1 terabyte USB connected
* 1 is a 9gb firewire

My two questions are:

Are there particular settings for external hard drives ?
The usb one is auto mounted as getphuture:root with permission rwx------ Works good
The firewire one is auto mounted as 99:99 rwx---rwx which is weird. I can't touch anything, only reading. It was previously used with an other mac for auto-bakckup. 

How can I easily share those hard drives on the LAN ?
I should use samba, right ? From now I follow some tutorials to setup samba manually.
I set up samba with permissions for the user getphuture.
How to add the devices ? In an easy way, like is there a GUI or an other tool available ?

Any help appreciated

---

### Post by getphuture on 2012-04-15
For the issue with 99:99,  I used a software called "gparted" to reformat and rename the disk. Works like a charm. Not shure I understood everything, it looks to happen when the disk was used by an other system ( Wndows, or Mac in my case ) and those permissions can't be used in Linux so it's auto-mounted as read-only. 

For samba I had to dig a little bit deeper and successfully set up samba via editing the conf files. If someone knows a way to modify the settings via a GUI, I'm still interesting :-)

---

