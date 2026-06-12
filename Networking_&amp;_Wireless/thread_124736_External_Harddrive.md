---
title: "External Harddrive"
date: 2006-02-02
forum: Networking &amp; Wireless
---

### Post by Maupertus on 2006-02-02
Hi,

I have an old PIII with a 40 Gig harddrive. Now my roommate and I had the idea of making it into an external harddrive. But is it possible to turn it into one, that can be accessed both from a Linux(Ubuntu) and a Windows Computer? And how would one do such a thing?

---

### Post by mips on 2006-02-02
You basically want to turn the PC into a fileserver.

For windows PC's you will have to run SAMBA on the Server.
For Linux PC's run NFS on the Server. If you dont use nfs then you can always use the samba client on the linux pc's.

You can do a plain server install but you will have no gui, only cli. You can always add a ligh windows manager or something like xubutu desktop.

Do a search for SAMBA & NFS, you will probably fing Howto's in the custumization & tips forum.

---

