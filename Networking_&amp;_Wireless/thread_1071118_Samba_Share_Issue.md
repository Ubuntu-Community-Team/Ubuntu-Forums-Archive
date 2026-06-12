---
title: "Samba Share Issue"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by bobmendon on 2009-02-15
When I try to share a folder I get the following error:

Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.

What does this mean in real language? How do I fix it?

---

### Post by utnubuuser on 2009-02-16
Tried re-installing Samba?

How about > sudo dpkg --configure -ain a terminal?

---

