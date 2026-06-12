---
title: "[SOLVED] burning cds lasts too long and blocks the drive"
date: 2008-09-14
forum: Multimedia Software
---

### Post by ejv on 2008-09-14
Hi

I've got Hardy Heron.  Each time I burn a cd from brasero or rythmbox the finalizing process is extremely long (about 20 minutes)..  At the end the process finishes successfully but the drive won't open until i restart the computer.  

Where should i look for the problem?

Thanks

ejv

---

### Post by cariboo on 2008-09-14
Can you eject the cd from the command line?

```
sudo eject /media/cdrom
```

Jim

---

### Post by ejv on 2008-09-15
Hi

I read your message only after i had already restarted the pc.  After the restart and before booting i was able to open the tray manually.  I'll have to give it a try later once more.

ejv

---

### Post by ejv on 2008-09-16
Hi Jim

The tray won't open when i type 

sudo eject /media/cdrom

ejv

---

### Post by ejv on 2008-09-20
Now it's all working fine.  See

[http://ubuntuforums.org/showthread.php?t=924227](http://ubuntuforums.org/showthread.php?t=924227)

ejv

---

