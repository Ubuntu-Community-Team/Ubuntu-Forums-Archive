---
title: "[SOLVED] Samba shares not in smb.conf"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by agibby5 on 2008-12-12
I am having an issue with samba showing shares that aren't defined in my smb.conf file.  

For example, I have one share named "share".  It's showing up when I browse the computer's shares.  However, I'm also seeing another share called 'apps' and another called 'working'.  Where else would these be defined so that they can be removed?

Here's a copy of my smb.conf file:

```

[share]
	path = /media/sdc1/share
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

[global]
;	wins support = no
	workgroup = workgroup
;	server string = samba 3.2.3
	security = share
;	encrypt passwords = yes
	guest ok = yes

```

Thanks.

---

### Post by Iowan on 2008-12-12
Check /var/lib/samba/usershares

---

### Post by agibby5 on 2008-12-12
> **Iowan said:**
> Check /var/lib/samba/usershares

That was it! Removed the files contained inside, restarted samba, golden! Thanks so much.  How would those files have gotten there?

---

### Post by bab1 on 2008-12-12
> How would those files have gotten there?

They appear there because you used Gnome Nautilus to create the shares.  When you use Nautilus you are using the gvfs libs to configure Samba instead of the smb.conf file.

---

