---
title: "SSH and nautilus"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by Cue2 on 2009-12-27
I've used x forwarding and ssh to access my remote machine. I run nautilus on the remote machine but I cannot access any network locations or even the windows partition. I get the error "nautilus cannot handle smb location" or "nautilus cannot handle computer locations"

I can however access it when sat at the machine or using smbclient. why can't I access them from nautilus remotely?

---

### Post by Cue2 on 2009-12-28
nobody knows why?

I just connected to a scientific linux machine and nautilus can access everything but on my ubuntu machine nautilus can't do much at all.

---

### Post by puppywhacker on 2009-12-28
gksudo "dbus-launch nautilus --no-desktop --browser"

---

### Post by Cue2 on 2009-12-28
> **puppywhacker said:**
> gksudo "dbus-launch nautilus --no-desktop --browser"


thanks. That command is way over my head but I can now access the locations remotely. one thing that bothers me though is that it seems to be with the root account.

---

