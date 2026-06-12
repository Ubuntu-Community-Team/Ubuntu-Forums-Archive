---
title: "Permissions cannot be determined over samba share"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by SpeedoJoe on 2013-02-20
I have shared a drive with the below command...
```

sudo net usershare add archive /mnt/archive/ "" everyone:r guest_ok=y

```The file is not viewable with VLC via Nautilus' Samba support on the client but is viewable on the server. The server shows the below permissions.
[IMG]http://i.imgur.com/wjkPCsz.png[/IMG]
```

-rwxrwxr-x 1 local local 5863920384 Feb 20 16:21 file.mkv

```/var/lib/samba/usershares/archive```

#VERSION 2
path=/mnt/archive/
comment=
usershare_acl=S-1-1-0:R
guest_ok=y
sharename=archive

```Have I missed something?

---

### Post by SpeedoJoe on 2013-02-22
Bump. No idea?

---

