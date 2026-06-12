---
title: "Mounting NAS after wireless gets up"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by hashimoto on 2009-01-24
A need a a little help with this:

I have a NAS that mounts fine with the following line in fstab:
```
//machinename/share /local/path/to/mountpoint cifs credentials=/root/.smbcredentials,iocharset=utf8	   0	0
```

The problem is with my wife's laptop and using wireless. Wireless comes up only after logging in and thus, the NAS does not get mounted. For me this is not a problem as I can do:
```
sudo mount -a
```

However, my wife is a normal user, doesn't have sudo powers and doesn't want to use cli, either. So I need a script or something that I can place on her desktop so she can click it and mount the NAS after the wireless comes up.

Any ideas?

---

### Post by hashimoto on 2009-01-26
Bump

---

