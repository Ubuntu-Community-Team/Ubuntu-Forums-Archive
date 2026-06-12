---
title: "Brasero Disc Burner not working"
date: 2012-11-19
forum: Multimedia Software
---

### Post by kuchakra on 2012-11-19
Hi I wanted to burn one DVD with .iso file using brasero but its not working. Showing an error ubuntu 12.04 error while burning  SCSI error on write(16,16): [3 0C 00] Write error

---

### Post by ibjsb4 on 2012-11-19
Try a different burner.  I like k3b, its in the software center.

---

### Post by kuchakra on 2012-11-19
k3b also not working!:(
> **ibjsb4 said:**
> Try a different burner.  I like k3b, its in the software center.

---

### Post by ibjsb4 on 2012-11-19
Are you getting any errors with k3b?  Also this may help:

[http://www.kde.org/applications/multimedia/k3b/](http://www.kde.org/applications/multimedia/k3b/)

---

### Post by andrew.46 on 2012-11-19
Try from the commandline in case both of the guis have a problem (unlikely):

```

growisofs -dvd-compat -Z /dev/dvd=burn_me.iso

```

You will have to replace *burn_me.iso* with the name and path of your iso and perhaps also change* /dev/dvd* to the correct path to your dvd drive.

---

### Post by mwl128340 on 2012-11-20
i had a similar problem. i found that if the write speed is set to automatic itll try and write to a different speed than my drive. i found the highest speed for dvd burner and set it in the options instead of auto and has burned flawless since.

---

