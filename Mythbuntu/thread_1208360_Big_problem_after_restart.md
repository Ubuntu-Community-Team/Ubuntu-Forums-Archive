---
title: "Big problem after restart"
date: 2009-07-09
forum: Mythbuntu
---

### Post by axelsvag on 2009-07-09
After a restart of the mythtv box with amd 64 I got in to big problems. The boot process just stops after 5 s and the led at the front shows that the HD  is intensive. After about 9 min I get a message that says something like this 
"
/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e. without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 0% (stage 1/5, 0/3680)

*An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
 The fsck should be performed in maintenace mode with the 
root filesystem in read-only mode. "

Ok I did what it said fsck and said a few hundred times and then after 25 minutes I was up and running again. I wonder what caused the error the first place?

I am not really sure what to do?

---

### Post by klc5555 on 2009-07-09
> **axelsvag said:**
> After a restart of the mythtv box with amd 64 I got in to big problems. The boot process just stops after 5 s and the led at the front shows that the HD  is intensive. After about 9 min I get a message that says something like this 
"
/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e. without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 0% (stage 1/5, 0/3680)

*An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
 The fsck should be performed in maintenace mode with the 
root filesystem in read-only mode. "

Ok I did what it said fsck and said a few dundred times and then after 25 minutes I was up and running again. I wonder what caused the error the first place?

I am not really sure what to do?

A dirty shutdown or reset can do it, power interruption or power-supply problems, or any of a number of things that might cause file corruption or cross-linked files on the root file system. It could also be the drive preparing to die.

So, make appropriate backups, just in case. If, while making sure to do only clean shutdowns and restarts, the problem doesn't return, then you know it was a isolated event. Hooray! But if the problem begins to happen with some frequency, get ready to replace the drive. If the problem is coupled with other events, like weird memory errors and lockups, or spontaneous reboots, then begin to suspect the power supply.

---

### Post by axelsvag on 2009-07-10
Thank you I will take your advice and do some new backups. You never know.

---

