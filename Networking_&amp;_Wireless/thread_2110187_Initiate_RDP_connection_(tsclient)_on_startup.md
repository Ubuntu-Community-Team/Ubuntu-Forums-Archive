---
title: "Initiate RDP connection (tsclient) on startup"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by kgermann on 2013-01-29
Hey guys - Novice Linux user here, n00b to the forum.

What I am trying to accomplish, is create dummy terminals for a shop wherein Ubuntu 10.04 LTS 686i machines are deployed to track jobs. The only peripheral device that will be connected is a barcode scanner.

Now, what I'm really here for:

On startup, I can create a task called tsclient which starts the Terminal Server Client immediately after boot, however, that's all it'll do. I want immediately after boot, for the computer to connect to an RDP connection (Windows Server 2003, Terminal Server) with whatever credentials I want.

I am going to assume it starts as:

```
tsclient -somethingsomethingsomething
```

Any help would be appreciated.

---

### Post by aromo on 2013-01-29
I suggest you create a non-admin user, set it up to log on automatically (not asking for password), and change the shell from /bin/bash to /path/to/tsclient -somethingsomething (could do this last one by editing /etc/passwd).

---

