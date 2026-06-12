---
title: "I buggered up - Mount point for iPod :("
date: 2009-03-12
forum: Multimedia Software
---

### Post by Ausmosis on 2009-03-12
Hi,

does anyone know how I can mount my iPod again. I was silly by  right clicking on my iPod desktop icon, then went into properties and changed the mount point. By doing that I'm now unable to mount my iPod and I lost the desktop icon (obviously because the ipod won't mount) and cant change back to the correct mount point. 

I assume there is a file I can edit to try and revert the mount point name so that the ipod can mount again??

Thanks!

---

### Post by aeiah on 2009-03-12
its probably in your fstab. you could try creating the directory you set as the mount point. perhaps the only reason it isnt working is because the new mountpoint folder doesn't exist

---

### Post by sonnychee on 2009-03-16
Hey Guys,

I have the exact same problem.  Nothing in the /etc/fstab file for ipod.  My exact error message is:

"mount_point can not contain the following characters: newline, G_DIR_SEPERATOR (usually /)"

Any help would be really appreciated.

---

### Post by mc4man on 2009-03-17
See here
[http://ubuntuforums.org/showthread.php?p=6905567#post6905567](http://ubuntuforums.org/showthread.php?p=6905567#post6905567)

Basically see if there is an entry in either drive or volume (depends on which you choose in properties)
If you find one corresponding to the ipod, right click on the mount_point entry and choose unset

---

### Post by sonnychee on 2009-03-18
Thanks for the pointer mc4man!  I fired up 

> gconf-editor

and then reset the value under system->storage->drives.

Sweet, that fixed the issue.

---

