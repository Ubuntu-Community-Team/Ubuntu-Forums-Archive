---
title: "cifs and swedish chars?"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by ftornell on 2011-10-17
Hi,
Trying to set up a cifs connection in fstab to my NAS (Synology DS211).

Everything is working fine except that the characters is crappy, guess that has to do with he charset...

I have tried various things but I need assistance.

This is how it looks now:
```

# NAS Share
//192.168.0.80/photo    /media/NAS      cifs    iocharset=utf8,credentials=/home/fredrik/.smbcredentials,file_mode=0775,dir_mode=0775        0       0

```

Have tried:
- iocharset=iso8859-1
- codepage=iso8859-1
- codepage=cp850
- a combination of iocharset=utf8, codepage=iso8859-1

Please advice!

---

### Post by capscrew on 2011-10-17
> **ftornell said:**
> Hi,
Trying to set up a cifs connection in fstab to my NAS (Synology DS211).

Everything is working fine except that the characters is crappy, guess that has to do with he charset...

I have tried various things but I need assistance.

This is how it looks now:
```

# NAS Share
//192.168.0.80/photo    /media/NAS      cifs    iocharset=utf8,credentials=/home/fredrik/.smbcredentials,file_mode=0775,dir_mode=0775        0       0

```

Have tried:
- iocharset=iso8859-1
- codepage=iso8859-1
- codepage=cp850
- a combination of iocharset=utf8, codepage=iso8859-1

Please advice!

The rendering is the responsibility of the local OS.  The mount directives are only for *mounting * the share.  The directive *iocharset * is for determining the charset that is used for the **path to the share** not what is in the share.  The codepage directive is from the now deprecated *smbmount *.  Mount.cifs ignores that.

---

### Post by ftornell on 2011-10-18
In other words, what do I need to change on my Ubuntu Server 11.10 that want's to connect to my NAS.

Do I have to change some charset on Ubuntu? I tried to choose sv_SE or what its called but that was not supported during the installation.

Do I need to change anything in my fstab line?

---

### Post by redmk2 on 2011-10-18
> **ftornell said:**
> In other words, what do I need to change on my Ubuntu Server 11.10 that want's to connect to my NAS.

Do I have to change some charset on Ubuntu? I tried to choose sv_SE or what its called but that was not supported during the installation.

Do I need to change anything in my fstab line?

I would start with commenting out the line in the fstab file and then trying to mount the NAS share with Nautilus (if you are using Gnome) or whatever file browser you are using.

This will use (in Gnomes case) the GVFS virtual file system.  It will mount the share at ~/,gvfs.

See if your UTF-8 characters render correctly.

At this point we are really just diagnosing the problem, so failure is not a bad thing.

---

