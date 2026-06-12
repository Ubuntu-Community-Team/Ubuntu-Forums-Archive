---
title: "Missing files in /etc/samba"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by mannequin on 2009-05-24
Hi all,

I'm wondering if there is an easy way to replace all of the default files in /etc/samba?

A little background:  I've been noticing for the past two or three days that winbind has been failing on startup.  Further inspection revealed that it couldn't open smb.conf.  Taking a peek in /etc/samba, further revealed that the directory was empty.

I've been able to replace smb.conf through the use of the sample one found in /usr/share/samba, but I need to replace the other files that are there after a fresh install (without doing a fresh install.)

Thanks,
-M.

---

### Post by Iowan on 2009-05-24
My */etc/samba* directory contains four files: 
smb.conf - pruned, working copy
smb.conf.bak - backup copy
dhcp.conf - empty on Gutsy machine, conatins "wins server ==" on Jaunty box
gdbcommands - contains two lines "bt", and "quit"

---

### Post by mannequin on 2009-05-29
Thanks for your help.  :)

---

