---
title: "smb printing issues"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by erictherev on 2009-02-27
As the title implies, I am having difficulties printing over smb. I have a HP LaserJet 6P connected to my Kubuntu system and am attempting to have it print over a smb (Windoze) network. I can print from the Kubuntu system, and I can see the printer from the Windoze systems, but under the icon on the Windoze systems it says, "Access denied, unable to connect"

Here is the printing section of my smb.conf, if it helps:
```
; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

```

As always, any and all help is greatly appreciated.

---

