---
title: "Sharing directories confusion..."
date: 2011-04-27
forum: Mythbuntu
---

### Post by phroman on 2011-04-27
Hello all, I have a sharing question.  I would like to share a folder on my second hard drive, /drive2/share1.  If I right click on it, I can select Share This Folder, give it a name, click the button to share it, done. The icon changes to one with arrows, all seems well.  This share does not show up in my /etc/samba/smb.conf.

From my other ubuntu machine, using nautilus I can browse the network and see the share1 directory, but am asked for a password which is rejected every time.  The other standard mythbuntu shares listed in smb.conf are accessible without a password.  So what's controlling this share.  I thought it may be NFS but I do not have an /etc/exports file.  I don't mind adding it to my smb.conf but I'd really like to know what's happening with this.  Thank you very much in advance.

---

### Post by ian dobson on 2011-04-27
Hi,

Why not just manualy edit your smb.conf file and add the share there.

Regards
Ian Dobson

---

### Post by phroman on 2011-04-27
Hi Ian, yeah, I'll probably do that, but it's a little disconcerting that something is sharing this directory and I have no idea what or how to control it.  Is it possible that another instance of samba is running or something like that?  Thanks again.

---

