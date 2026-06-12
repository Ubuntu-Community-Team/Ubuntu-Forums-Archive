---
title: "How can I share Samba in Virtualbox?"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by hopelessone on 2010-09-15
Hi,

Ubuntu 10.04 with Windows OS as Virtualbox, using Samba I connected to another computer which shows up mounted as: ```
smb://scott/premier9/
``` Now in Virtualbox Shared folders it doesn't show up so I can't share it?

Screen shots below...

How can I See it in Virtualbox?

Many Thanks

---

### Post by hopelessone on 2010-09-15
I tried mounting it to a folder:
```
smbmount //scott/premier9/ /home/samba -o rw
mount error: could not resolve address for scott: No address associated with hostname
No ip address specified and hostname not found
erg@erg-parts:~$ 

```

How can i find the ip address?

Taa

---

