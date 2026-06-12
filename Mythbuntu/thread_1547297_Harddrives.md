---
title: "Harddrives"
date: 2010-08-06
forum: Mythbuntu
---

### Post by jrhartley on 2010-08-06
Im just coming over from Mythdora 5. I installed the latest mythbuntu (10.04)but it only uses the first harddrive. mythweb is only seeing 100gig. I have a 250 gig secondary drive that it is not reporting.

---

### Post by newlinux on 2010-08-06
When you say the drive is not reporting what do you mean? Where are you looking that you do not see it?

what do:

```

sudo fdisk -l

```
and
```

df -h 

```

Is it an internal (sata/IDE) or external (USB/Firewire/Esata) drive?
return

---

