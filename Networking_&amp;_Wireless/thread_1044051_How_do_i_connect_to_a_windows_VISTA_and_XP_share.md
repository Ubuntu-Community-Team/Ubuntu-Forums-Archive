---
title: "How do i connect to a windows VISTA and XP share?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Jynks on 2009-01-19
Hi... I think i have got smaba installed... but i am not sure...

from my XP system i can browse the network and I can see my xbuntu computer ... but it is in "workgroups" while my home workgroup has a different name.

1) How do I change the "workgroup" so on my XP system the computer is in teh correct workgroup instead of in the generic named "workgroup"/

2) How do i browse the windows network from my Xnbuntu system and acess the shares on teh XP systems?

Thanks in advance
Jynks

---

### Post by Iowan on 2009-01-19
Workgroup *should* be in /etc/samba/smb.conf under Global Settings.

I tried changing the setting in this workstation's file, but as there is no /etc/init.d/samba (this machine shares no files) I'm not sure if it will help.  There's also a System>Administration>Networking option (on this Gutsy machine) to set the Domain name... though I've never been able to make it stick.

---

