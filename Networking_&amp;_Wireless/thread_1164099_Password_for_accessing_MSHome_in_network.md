---
title: "Password for accessing MSHome in network"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Hagar55 on 2009-05-19
I have a wireless network with an older desktop running WinXp.
The network works just fine in Windows Vista.
If I select Network in ubuntu, I can see the icon "Windows Network"
,when I go there I can see MSHOME and WORKGROUP, when I try to log into MSHOME Ubuntu asks for a password, wich password is required here ?

---

### Post by superprash2003 on 2009-05-19
its better to use advanced file sharing in windows xp .. [http://support.microsoft.com/kb/307874](http://support.microsoft.com/kb/307874)

---

### Post by Hagar55 on 2009-05-19
Ok, I don't want to go fooling around with permissions right now.
Do I need Samba to acces my home network? 
I don't remember having to set a password on my windows home network, or is that the password I need to acces the wireless network ?

Do I need to changemy workgroup name somewhere in Ubuntu ?

---

### Post by Iowan on 2009-05-19
> **Hagar55 said:**
> Do I need to changemy workgroup name somewhere in Ubuntu ?
I usually manually edit */etc/samba/smb.conf*, but the information may be available via GUI somewhere. I did a quick scan of my laptop (Jaunty) but didn't see it right away.

---

