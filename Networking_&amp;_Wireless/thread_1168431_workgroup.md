---
title: "workgroup"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by yanosj on 2009-05-24
I just put 9.04 on a new machine and I'm having trouble with windows workgroups.  The linux machine sees everybody on my network (windows and linux) and they all see the new machine.  I changed the workgroup name on the new machine in /etc/samba/smb.conf to "mygroup" but they all still see it as "workgroup".  I don't see anyplace else to reset it.  What did I miss?

Thanks

---

### Post by Iowan on 2009-05-24
Did you restart the machine (or at least Samba) after changing the workgroup?

---

