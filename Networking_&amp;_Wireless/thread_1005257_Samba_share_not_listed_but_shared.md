---
title: "Samba share not listed but shared"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Rauchen on 2008-12-08
I have mounted an NTFS drive (Data1) and I shared it using the sharing option that comes with Ubuntu 8.10 which is Samba. For some reason it didn't show as share the next time I rebooted so I shared it again but under a different name. I found out later that it was already shared and now there are two shares on the network for the same folder. This is really annoying and I can't figure out where Ubuntu is storing this info because I looked under System->Administration->Samba and there are no listings there even though I have share quite a few folders.

Any help would be appreciated :)
Thanks in advance.

---

### Post by Iowan on 2008-12-08
In olden days (when I understood things), *all* share info was in /etc/samba/smb.conf.  Nowadays, some shares seem to be stored in /var/lib/samba/usershares - although the smb.conf still seems to work, too.

---

### Post by Rauchen on 2008-12-08
Oh man thanks a lot Iowan! That was exactly where they were. \\:D/

Cheers and have a merry Christmas and a happy new year!

---

