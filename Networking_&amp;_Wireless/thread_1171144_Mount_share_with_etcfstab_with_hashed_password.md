---
title: "Mount share with /etc/fstab with hashed password"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by dentharg on 2009-05-27
Hi!

Currently I have cleartext password in my /etc/fstab to mount a windows share. However I'd prefer to have it in encrypted form.

Is it at all possible?

---

### Post by dmizer on 2009-05-27
Neither samba server nor the CIFS daemon support encrypted passwords.

Your best bet is to use a credentials file that's only viewable by root. Instructions for this can be found in the second link in my sig.

---

### Post by dentharg on 2009-05-27
Thanks! This will do.

---

