---
title: "problem starting samba"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by galileon on 2006-06-30
hello everyone,
I'm trying to get a samba server running to share files with my windoze laptop,

when i do $sudo smbd - D

then ps -A, smbd is not listed

$cat /var/log/samba/log.smb d gives the following:

[2006/06/30 13:23:18, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/06/30 13:23:18, 0] lib/util_sock.c:open_socket_in(826)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use


any ideas how to get it running? thanks!!

---

### Post by galileon on 2006-06-30
solved!! i had installed inetd which i have now removed

---

