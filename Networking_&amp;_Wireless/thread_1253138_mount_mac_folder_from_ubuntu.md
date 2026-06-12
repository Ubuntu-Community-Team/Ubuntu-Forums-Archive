---
title: "mount mac folder from ubuntu ?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by cbear on 2009-08-29
I am trying to mount a folder on my mac from Ubuntu so I can run weekly backups of my mac files via an rsync script. I have several windows machines mounted from Ubuntu, but never tried a mac.

I tried

Code:

mount -t nfs //<ip of the mac>/folder /media/mymac

tried "cifs" too...doesn't work.

Do I need something special to mount a mac folder ? Works like a charm from on windows machines.


thanks

---

### Post by cbear on 2009-08-29
just tried this...thinking it was 'smbfs'.  Does not work either.

```
 mount -t smbfs -o credentials=/root/.smbcredentials3 //192.168.1.203/ITunes/ /media/mac/
```

---

### Post by cbear on 2009-08-29
got it working:

```
mount -t smbfs -o credentials=/root/.smbcredentials3 //192.168.1.203/Music /media/mac
```

The path was not valid before (folder name).

---

