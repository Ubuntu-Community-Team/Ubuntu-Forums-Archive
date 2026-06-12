---
title: "Samba. Workgroup. Auto-authenticate?"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-10-03
My Ubuntu desktop works as a backup server, since I have hard drives in it dedicated simply for Samba backups for the XP users in the house.

I don't have a domain or anything like that. I just simply have Samba installed and shares made for each of the users. Everybody is in workgroup "WORKGROUP." Creative, I know.

Is there any way I can have their local accounts auto-authenticate to log in to their Samba shares? That way if I log in as Fred on his PC, when I go to start - run \\SambaServer then they won't have to log in again - they'll be granted access due to Fred's local XP login.

Is that possible?

---

### Post by kreggz on 2009-10-06
if you mount the share in fstab you could do it

[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

