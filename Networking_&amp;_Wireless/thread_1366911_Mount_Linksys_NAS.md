---
title: "Mount Linksys NAS"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by wolfsong on 2009-12-28
I'm running 9.10 and would like to mount the share on my Linksys NAS. I tried to follow [this]("https://help.ubuntu.com/community/SettingUpSamba") but I think I might be missing something simple.

I created /etc/Samba/user with
```
username=guest
password=
```

and I added the following to /etc/fstab
```
"//192.168.1.199/Public disk" /media/samba_share  cifs  noauto,credentials=/etc/samba/user,noexec  0 0
```

I tried mounting at this point but I get 
> [mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/samba_share in /etc/fstab or /etc/mtab

Any ideas? Thanks.

---

### Post by dmizer on 2009-12-28
Try this:
```
sudo mkdir /media/samba_share
```
Then run sudo mount /media/samba_share again.

Also, change your /etc/fstab line to this:
```
//192.168.1.199/Public\040disk /media/samba_share  cifs  noauto,guest,rw,noexec
```

---

### Post by wolfsong on 2009-12-28
> **dmizer said:**
> Try this:
```
sudo mkdir /media/samba_share
```
Then run sudo mount -a again.

Sorry. I created the share as well so that's not the problem.

---

### Post by dmizer on 2009-12-28
> **wolfsong said:**
> Sorry. I created the share as well so that's not the problem.

Please see my edit with updated /etc/fstab line. :)

---

### Post by wolfsong on 2009-12-28
> **dmizer said:**
> Please see my edit with updated /etc/fstab line. :)

That worked. Thanks!

---

