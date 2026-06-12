---
title: "How to automatically sync Samba passwords with user account passwords"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by kooldino on 2010-04-27
Figured other people would find this helpful:

> 
The pam_smbpass PAM module can be used to sync users' Samba passwords with their system passwords when the passwd command is used. If a user invokes the passwd command, the password he uses to log in to the Red Hat Linux system as well as the password he must provide to connect to a Samba share are changed.

To enable this feature, add the following line to /etc/pam.d/system-auth below the pam_cracklib.so invocation:

password required /lib/security/pam_smbpass.so nullok use_authtok try_first_pass


---

### Post by dannyboy79 on 2010-04-27
should be moved to tutorials.

---

