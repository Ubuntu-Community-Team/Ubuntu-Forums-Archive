---
title: "network file sharing options? not NFS"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2009-04-23
Hi

If I have an Ubuntu server with Ubuntu clients (all 8.04), what are my options for sharing OpenOffice files from the server to the clients. The share **must** be able to lock an office file if someone else is editing it.

So far I've tried NFSv3 and NFSv4 for this but couldn't find a way for it to lock the files when they are in use

what other options are there? 



thanks

---

### Post by pytrisss on 2009-04-23
I think samba is able to lock files, but never tried it.
[http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html](http://de.samba.org/samba/docs/man/Samba-HOWTO-Collection/locking.html)

But samba is also bit slower then NFS or the others.

---

### Post by beaker15 on 2009-04-23
I used samba when I used to have WinXP clients and it did lock files when they were in use but i wasn't sure if Windows was locking the file or if Samba was doing it. I did'nt really want to use Samba since I don't have any Windows clients but if it works I'll be happy so its worth a try. 

I am still open to suggestion on any other options though

thanks

---

