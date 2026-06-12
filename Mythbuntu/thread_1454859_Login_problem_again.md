---
title: "Login problem again"
date: 2010-04-15
forum: Mythbuntu
---

### Post by nunrgguy on 2010-04-15
After upgrade to Karmic many months back I had the multi login problem - an endless loop of trying to log in and getting kicked back to the login screen. The solution I fond was not the one most people found on here. It turned out that the desktop theme was corrupted. After changing the theme I no longer had the problem.

After bootnig up this morning, after many months of successful operation I have the log in problem again.

Now, I can fix this by VNCing in and changing the theme to another one but...eventually i am going to run out of themes to change to.

Any ideas which file is getting corrupted and why?

---

### Post by nunrgguy on 2010-04-15
Scratch that - am unable to VNC in and can't log into any of the other desktops either

---

### Post by vladilinsky on 2010-04-15
I have what is potentially the same problem, for me the temporary solution until i figure out what is happening is i need to manually mount ( sudo mount /dev/sda5 /home ) my home partition.   for some reason after the update to the mythbuntu beta it no longer mounts my home partition at boot.   hopefully that helps

---

### Post by nunrgguy on 2010-04-15
Hmm, not certain if that will be it - I've not done any updates etc. Just logged off last night, then this morning couldn't log in. If I leave it at the log in screen or boot into terminal I can see  all of my samba shares across the network it's jsut the boot into the desktop I can't get. startx just gives a bunch of errors

---

### Post by nunrgguy on 2010-04-15
Right - I think I've figured out what the problem is -  x is unable to open a temp file as disk space has run out. System is only installed on a small 20 gig drive with rest data in an lvm. Was deleting data last night in Thunar and it's shifted to wastebasket and filled the drive up.

Anyone know how to empty Thunar's wastebasket from Terminal?

---

### Post by nunrgguy on 2010-04-15
Figured it out .local/shared

Only problem now is I've found out one of the drives in the lvm is on its way out...pah!

---

### Post by Lepy on 2010-04-16
Glad you sorted out your problem. The times I have encountered a login loop/problems has been due to a full disk.

---

