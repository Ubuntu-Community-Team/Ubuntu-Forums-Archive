---
title: "Samba and 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by bikeboy24 on 2009-11-01
I'm having a weird issue with trying to get printer sharing using samba. On a fresh boot, fileshares will be working fine, however printer sharing does not work. If I restart samba, everything works fine (including printer sharing).
 
 
Sample output from log.smbd
 
[2009/10/31 12:24:51, 0] smbd/server.c:1068(main)
smbd version 3.4.0 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/10/31 12:24:51, 0] printing/print_cups.c:103(cups_connect)
Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/31 12:24:51, 0] printing/print_cups.c:103(cups_connect)
Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/31 12:24:54, 0] smbd/server.c:456(smbd_open_one_socket)
smbd_open_once_socket: open_socket_in: Address already in use
[2009/10/31 12:24:54, 0] smbd/server.c:456(smbd_open_one_socket)
smbd_open_once_socket: open_socket_in: Address already in use
 
Any ideas?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
could be a bug id try reporting it and looking for solutions

---

### Post by winz on 2009-11-06
Just to confirm, I have the same issue on 9.10. I put "service samba restart" to /etc/rc.local as a temporary workaround.

---

