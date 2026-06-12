---
title: "How to undo the INSMOD command"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by mtbuller on 2006-06-30
while trying to get my usb adapter working, I had followed the instructions and built the driver and issued the command  $insmod /somedirectory/rt73.ko

now that the driver don't work and I rebuilt another driver but noticed that the previous driver is automatically loaded upon bootup even after I had deleted the rt73.ko file and directory.

I had tried surfing the net but unable to get the info to "undo" the insmod command.

any experts around that knows how to do it .

many thanks in advance.

:confused:

---

### Post by mlind on 2006-06-30
rmmod could work, or modprobe -r

---

### Post by mtbuller on 2006-06-30
[QUOTE=mlind]rmmod could work, or modprobe -r[/QUOTE]

THANKS

---

