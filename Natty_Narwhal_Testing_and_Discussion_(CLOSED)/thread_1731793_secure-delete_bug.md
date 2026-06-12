---
title: "secure-delete bug?"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yeeha on 2011-04-17
I wanted to clean my laptop before giving it up so i booted into kubuntu natty beta2 livedvd. Thougbugh secure-delete was not installed it seems you can install packages to ram? But after installing it, deleting everything i tryed to:

root@ubuntu:~# sfill /dev/sda
Error: /dev/sda is not a directory
Programming Error: sdel-lib was not initialized before calling sdel_finnish().

Any ideas or alternative solutions?

---

### Post by Yeeha on 2011-04-17
Hmm... it seems you cant use /dev/sda as target but setting target to mount point /media/* seems to work... I think... :D

---

### Post by pressureman on 2011-04-17
If you want to securely wipe hard disks before selling them or giving them away, I recommend Darik's Boot and Nuke [http://www.dban.org/](http://www.dban.org/)

It will do a block-level secure wipe, so you will need to install an OS again afterwards... if you want to.

---

