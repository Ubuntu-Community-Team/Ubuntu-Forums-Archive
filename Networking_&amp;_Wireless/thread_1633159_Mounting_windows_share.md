---
title: "Mounting windows share"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by mws604 on 2010-11-28
Within nautilus, I can see all the Win 7 computers and printers in my workgroup.   When  I try to open them,  I am prompted for a password.  This is the problem - no password or authentication is required.   To prove this I use fstab and created a mount point to a windows share as guest.   So I know I have samba set up properly.   Also, I can read and write to the ubuntu shares from the Windows PCs.   

Same problem when trying to print - I am prompted for authentication even though it isn't required. Is  there anyway to eliminate the authentication process in nautilus and a shared printer?

Thanks in advance for any advice.

---

### Post by mws604 on 2010-11-29
Note that 'guest ok = yes' is set in smb.conf

---

### Post by mws604 on 2010-11-29
This is the

---

