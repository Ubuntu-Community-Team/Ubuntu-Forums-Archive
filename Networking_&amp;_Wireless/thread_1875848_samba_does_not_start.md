---
title: "samba does not start"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by jimmybond on 2011-11-05
I'm sorry if there was a previous post on this topic.  If so, I was hoping someone can redirect me to that post.  My search did not find similar problems. :o

I'm on 11.10.  Is there a way to diagnose this problem I'm having where samba's GUI just asks me for my admin password and disappears?  The internet connection is working fine, so I'm guessing it must be a conflict problem or that the configuration files aren't configured properly.

Thanks in advance.

---

### Post by azmyth on 2011-11-05
Check the log files in /var/log/samba

---

### Post by jimmybond on 2011-11-06
Thanks for the reply.
It seems like there are a bunch of errors in many of these log files.
The beginning already looks like a bunch of trouble:

```
[2011/11/05 10:10:04,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/11/05 10:10:04.711210,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/11/05 10:13:06.234340,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3367 -- ignoring
[2011/11/05 10:19:45,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/11/05 10:19:45.978355,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/11/05 10:22:13,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/11/05 10:22:14.640102,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2011/11/05 10:22:14.640404,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
```

---

