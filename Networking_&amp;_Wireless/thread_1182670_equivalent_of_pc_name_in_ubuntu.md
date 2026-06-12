---
title: "equivalent of \\pc_name in ubuntu"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by XturnLGod on 2009-06-09
Hi all,

I've been using Ubuntu for a while now; have everything ironed out as far as software (except for stinking google which isn't releasing sketchup any time soon...). My problem is this:
In windows, when you go start, run, \\pc_name (or IP) you get a prompt for username and pasword.
In ubuntu, all the smb tools I've found have a common snag: they require me to manually enter the share name (which sometimes is unknown). Does anyone know of a tool that scans for smb share on a given computer, asks for my creds, and lists all available shares?

as usual, thank you all for your help.
If I've posted in the wrong area, sorry.

---

### Post by Lampi on 2009-06-09
> **XturnLGod said:**
> Does anyone know of a tool that scans for smb share on a given computer, asks for my creds, and lists all available shares?
findsmb will show you the ips of available shares
smbtree -N will show you the name of available shares
smbstatus  will show you the machines connected to your shares

best thing is you use nautilus or konqueror to find and connect to shares - like this you get the login screen you want. If you have a permanent share you could think about adding this one to your /etc/fstab

---

### Post by eldragon on 2009-06-09
under nautilus:
```

smb://[ip or pc name]

```

---

