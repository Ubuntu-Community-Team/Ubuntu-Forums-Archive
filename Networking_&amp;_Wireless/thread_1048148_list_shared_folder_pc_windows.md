---
title: "list shared folder pc windows"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by luca219 on 2009-01-23
hi everyone,
(ubuntu 8.4.1)
with nautilus, when I log in the network to a Windows PC does not see the  list of shared folders, but if I log in directly to a folder
eg: //pc-win/shared1 everything ok, 
but if I log //pc-win  is all empty.

any ideas?

---

### Post by superprash2003 on 2009-01-23
try this.. open two windows with smb://pc-win and if it still doesnt open try pressing F5.. this is a nautilus bug

---

### Post by luca219 on 2009-01-27
I tried, but it does not work

---

### Post by sedawk on 2009-01-27
You can try if the shares are listed with command line tool
smbclient, either "smbclient -L pc-win" or "smbclient -L pc-win -U user".

I'm not sure about a windows pc, but with samba you can turn off
the listing of shares (browsing?), so you explicitely need to
know the name of the share you want to connect to.

---

### Post by Another Monkey on 2009-01-27
I am probably repeating myself (and those who know better are probably rolling their eyes at me, but anyway...)

Is your Ubuntu firewall blocking broadcasts and SMB data from Windows?  I had this exact problem and also thought I had some Nautilus/gvfs bug until I sorted my firewall out.

All [explained here]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access").  I only found that post by sheer fluke.

It fixed it all for me.

---

