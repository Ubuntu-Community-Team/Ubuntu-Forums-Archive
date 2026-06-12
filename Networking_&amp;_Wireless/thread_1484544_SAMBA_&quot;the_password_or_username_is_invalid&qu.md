---
title: "SAMBA &quot;the password or username is invalid&quot;"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Milliways on 2010-05-15
I have a 9.10 installation that I am unable to connect with SAMBA.

Attempts to access this (from Windows XP) give an error "the password or username is invalid".

I can see the computer, but not connect.

The Ubuntu installation is set up with the same user and password I normally use, and the files are setup the same way. I even copied smb.conf from another installation which works.

I set up SMB when prompted by shares-admin.

Can anyone help

---

### Post by Iowan on 2010-05-16
Did you set up a _Samba_ user/password with **smbpasswd**?

---

### Post by Milliways on 2010-05-16
> **Iowan said:**
> Did you set up a _Samba_ user/password with **smbpasswd**?

Thanks. This worked.

I am still confused.
I remember doing this (and much else) when first trying to get SAMBA working on Ubuntu 7.10.

Setting up 9.04, 9.10 and 10.04 (on another computer) it seemed much simpler with the GUI, and I am sure I did not do this.

I am positive about 10.04, which I did a couple of weeks ago - although I did have to edit smb.conf to share other than my home directory.

---

