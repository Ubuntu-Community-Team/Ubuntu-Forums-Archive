---
title: "Adding a PC to a cross-platform network"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2009-10-03
I have a kubuntu 9.04 installation. I've already set up samba so that files can be shared with one windows PC. Now I want to add another windows PC to this simple network. How should I set about doing that?

---

### Post by mahela007 on 2009-10-03
Should the samba shares be visible to any computer I connect after I configure samba just once?

---

### Post by swerdna on 2009-10-04
> **mahela007 said:**
> Should the samba shares be visible to any computer I connect after I configure samba just once?

Yes

Check the same workgroup is used in Linux box/es as in windows box/es.
Check you use the same name resolution method as windows uses natively (broadcast name resolution). Set this parameter in the [global] stanza of the Linux box/es' smb.conf files:```
name resolve order = bcast host lmhosts wins
```

FFI: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

