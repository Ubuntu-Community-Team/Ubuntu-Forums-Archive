---
title: "Mounting windows shared folder"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by fesghelbahal on 2010-01-09
I just want to mount a shared folder and I use:

```
sudo mount -t cifs -o username=user-name //uwstdentweb/shared /mnt
```

but it says:

```
mount: wrong fs type, bad option, bad superblock on //uwstdentweb/shared,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

What does this error mean, and what should I do?

PS: I could mount the same folder with the same command in fedora!

---

