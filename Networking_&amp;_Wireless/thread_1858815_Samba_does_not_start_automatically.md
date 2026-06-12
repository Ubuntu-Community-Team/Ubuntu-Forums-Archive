---
title: "Samba does not start automatically"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by dj-digger on 2011-10-13
Hi,

i am relative new to Ubuntu 11.04 and try to setup a Samba Server. The server is running and working correctly but every mornig (when i start the server-pc), smbd does not start automatically. if i log in and type ```
/etc/init.d/smbd start
``` the server starts and everything is fine. But why not automatically? My Samba Version is 3.5.8

LogFile from today:
[QUOTE=/var/log/samba/log.smbd]

[2011/10/13 08:51:09,  0] smbd/server.c:1123(main) smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/13 08:51:09.846013,  0] printing/print_cups.c:108(cups_connect) Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/13 08:51:09.849861,  0] printing/print_cups.c:108(cups_connect) Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/13 08:51:09.937232,  0] smbd/server.c:1169(main) standard input is not a socket, assuming -D option
[/QUOTE]

So what shoud i do? thanks in advance. if you need more information, let me know i will try to provide.

---

