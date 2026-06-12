---
title: "Smb4K not workin properly"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by insence on 2005-12-21
Ok, I've set the files smbmount and smbunmout or whatever they are called to chmod777. But when I try acessing a windowsnetwork I get this errormessage:

libsmb based programs must *NOT* be setuid root.
9272: Connection to ****** failed
SMB Connection failed

Anyone can help? :p

---

### Post by jrickard on 2006-11-17
You know, it's very nearly a YEAR later and I get exactly the same thing you're getting.  Not a real helpful crew here in Ubuntu land as eleven months later nobody has helped you.

Jack Rickard

---

### Post by sdwood68 on 2006-12-09
Smb4k needs two files changed to SET USER ID too work properly

execute these to commands

```
sudo chmod +s /usr/bin/smbmnt
sudo chmod +s /usr/bin/smbumount
```

---

### Post by daller on 2006-12-13
Thank you! - This forum is great!

Please add further tweaks here:

[https://help.ubuntu.com/community/smb4k](https://help.ubuntu.com/community/smb4k)

---

### Post by kosson on 2007-02-04
Fab !
It works like a charm !

---

