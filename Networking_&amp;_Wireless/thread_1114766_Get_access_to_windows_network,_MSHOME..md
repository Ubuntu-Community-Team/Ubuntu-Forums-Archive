---
title: "Get access to windows network, MSHOME."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by naver on 2009-04-03
So i've been looking around and it just says to get samba, samba-common and add share through alt+f2, shares-admin, and i've configured so im in MSHOME, still I CAN'T access windows computers, only linux computers. But the windows computers can access my linux computer.

Anyone knows how to fix so I can access windows computer as well?

---

### Post by sgosnell on 2009-04-03
Have you set the sharing on the Windows computers properly?  You can't see the shared folders at all?

---

### Post by Iowan on 2009-04-03
Can you SEE the Windows boxes? If you know their address(es), try **smb://<ip-address>/sharename** in the location bar.

---

