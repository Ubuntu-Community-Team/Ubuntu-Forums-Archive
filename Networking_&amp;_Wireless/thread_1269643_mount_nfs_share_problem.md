---
title: "mount nfs share problem"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by styven on 2009-09-18
Hi there,

After years of trying I have managed to access a share from one linux pc to another, great news.
However, all excited I have now tried to get another pc to access the share also, but get an error mesage in the terminal, see screenshot.
I can still access the shared folder from the other pc so not sure what the issue is.
All pcs involved have fixed ip's
the server pc is 192.168.1.2
pc that can mount share is 192.168.1.4
pc that can't mount share is 192.168.1.3

I have attached also a screen of my etc/exports file.

Any thoughts appreciated.
Steve

---

### Post by styven on 2009-09-18
OOps forgot the screenshots:(

Will follow shortly all being well...........

---

### Post by styven on 2009-09-18
screenshots

---

### Post by hendrik_ebber on 2009-10-05
Hi.
I had the same error as in your screenshot:
install nfs-common on your client.
```

sudo apt-get install nfs-common
```

Had me stumped at first because I just assumed that would be installed by default.


hth.


Hendrik

---

