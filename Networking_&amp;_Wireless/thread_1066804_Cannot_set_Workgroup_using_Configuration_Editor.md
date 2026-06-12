---
title: "Cannot set Workgroup using Configuration Editor"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2009-02-11
When I try to set the Workgroup using Configuration Editor (gconf-edit) via system > smb > workgroup, this change is not reflected in the /etc/samba/smb.conf file. So my workgroup remains unchanged.

Is this a known bug or is there some fiendish trick to using gconf-edit?

---

### Post by superprash2003 on 2009-02-11
why cant you directly change it in the smb.conf file

---

### Post by SteveDee on 2009-02-11
> **superprash2003 said:**
> why cant you directly change it in the smb.conf file

I can, and I have :P.

Its just that in other threads in this forum you will see the conf-editor approach recommended. And setting it in conf-editor certainly does something, because when I tried to access a 'buntu folder from my Windows laptop it correctly saw the group "UBUNTU" but asked for a password for the bogus group "BUNS"

Also, you can enter a Workgroup name running conf-editor as user and a different workgroup name when running conf-editor as root (gksu).

Its all rather odd! But like many variables in conf-editor, maybe its not fully implemented yet.

---

