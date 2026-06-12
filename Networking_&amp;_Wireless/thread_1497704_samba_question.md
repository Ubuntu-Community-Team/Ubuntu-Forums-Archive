---
title: "samba question"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2010-05-30
Hi
what do i need to do to get samba to use the tdbsam backend?.Is it just a matter of including the line:
```
passdb backend = tdbsam
```
in smb.conf?
I mean can you just add this line to smb.conf then use pdbedit to set up the accounts and that's it as far as setting up samba to use tdbsam as the database backend goes?.If not what else needs to be done?.I've googled this and the only thing i found said to use smbpasswd to set up the tdbsam backend.I just wanted to check if this was right.
Thank you for any replies

---

### Post by BoneKracker on 2010-05-30
Yes. Administer via pdbedit, and then manage user passwords with smbpasswd.

I think it's more complicated if you are using winbind.

---

