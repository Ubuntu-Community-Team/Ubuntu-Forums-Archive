---
title: "Where does samba mount the remote folder?"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-10-06
For instance, there is a computer 'box1' and a shared folder 'a', when I open nautilus > go > network > box1 > a the shared folder already auto mounted. But where is the mount point? The location only shows smb://box1/a/

Thanks in advance

---

### Post by Roasted on 2009-10-06
Just a guess - but have you checked your /mnt or /media directory?

---

### Post by mharrison on 2009-10-06
> **Roasted said:**
> Just a guess - but have you checked your /mnt or /media directory?


I have often wondered this myself, but never cared....but I did look when I had a network share open and /mnt and /media do not contain the network mount that I can see.  It might be when you browse to them and it "auto mounts" it is just linking to the network share.

---

### Post by lavinog on 2009-10-06
it should be under /home/username/.gvfs/sharename

---

### Post by afeasfaerw23231233 on 2009-10-07
Thanks. It is there.

---

