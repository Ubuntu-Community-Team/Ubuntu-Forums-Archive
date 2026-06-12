---
title: "Smaba and symlinks on host question"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2010-01-13
If I use Dolphin / nautilus to browse my host shares with my client machines, symlinks are followed like regular folders.  

If I use a regular mount command 

sudo mount -t cifs //192.168.15.100/Public /home/brian/Public -o with a string of options (mostly to give passwords, permissions, etc)

Symlinks on the host are show as broken. Is there any way to resolve this? Sometimes I need a hard mount point so that certain programs can find all files.  the smb:// as seen from dolphin or nautilus is not observed with most applications.

---

