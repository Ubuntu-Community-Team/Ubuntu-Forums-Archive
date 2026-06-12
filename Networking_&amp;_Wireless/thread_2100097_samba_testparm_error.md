---
title: "samba testparm error"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by oleink on 2012-12-31
Samba won't start and I've been googling for like an hour.  Testparm gives me this error:

> rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Error: Maximum include depth (100) exceeded!
Error loading services.


The first error from what I understand can be generally ignored because it is necessary for security purposes. But I could find absolutely nothing on maximum include depth try as I may.  Anyone have any clues??

---

### Post by redmk2 on 2012-12-31
> **oleink said:**
> Anyone have any clues??
How about a look at the /etc/samba/smb.conf file itself.

---

### Post by oleink on 2013-01-09
> **redmk2 said:**
> How about a look at the /etc/samba/smb.conf file itself.

Sorry I never replied.  I figured out the problem and feel extremely stupid.  You have to close the smb.conf file before starting the service (duh!).

---

### Post by redmk2 on 2013-01-09
> **oleink said:**
> Sorry I never replied.  I figured out the problem and feel extremely stupid.  You have to close the smb.conf file before starting the service (duh!).

Yes closing the file is important. ;-)

But we have all done that at one time or another.

---

### Post by oleink on 2013-02-21
> **redmk2 said:**
> Yes closing the file is important. ;-)

But we have all done that at one time or another.

Thanks again for the answers and encouragement

---

