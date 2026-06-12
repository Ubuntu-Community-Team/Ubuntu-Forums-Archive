---
title: "Repairing xorg.conf from Live CD"
date: 2010-07-19
forum: Mythbuntu
---

### Post by oldpgmr on 2010-07-19
I messed up my xorg.conf file and now the box stalls at the Mythbuntu screen.  I cannot seem to stop the frontend from starting to replace the xorg.conf with the backup copy.  Some posts indicate that this can be done by mounting location of the main partition using 

sudo mount /dev/sda1 /mnt

 but that is has not been successful.  

Is this possible to do from Live CD or is there a way to stop the frontend from starting?

---

### Post by superm1 on 2010-07-20
> **oldpgmr said:**
> I messed up my xorg.conf file and now the box stalls at the Mythbuntu screen.  I cannot seem to stop the frontend from starting to replace the xorg.conf with the backup copy.  Some posts indicate that this can be done by mounting location of the main partition using 

sudo mount /dev/sda1 /mnt

 but that is has not been successful.  

Is this possible to do from Live CD or is there a way to stop the frontend from starting?

You should be able to fix this also by just holding shift during boot and choosing the recovery option.  There is an option there for restoring X or for a root shell.

---

### Post by oldpgmr on 2010-07-20
That worked.  I had tried that first but my setup has a usb wireless keyboard so it would not accept the shift command.  Switching to a wired KB did the trick.

Thanks much

---

