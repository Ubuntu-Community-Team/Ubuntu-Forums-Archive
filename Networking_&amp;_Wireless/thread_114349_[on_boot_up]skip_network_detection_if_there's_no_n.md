---
title: "[on boot up]skip network detection if there's no network...how?"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by zahidism on 2006-01-08
ubuntu hangs for a while if there's no network (wireless, i set as default) when booting up.  is there any key i can press to skip boot up module processes.  also, if i do skip it, how can i get it going later on when there is a network available and the computer is already booted into ubuntu?  thanks.

---

### Post by DeadEyes on 2006-01-08
Ctrl c will allow you to bypass the process. You should be able to connect to the network later using iwconfig or one of the GUI network managers

---

### Post by Azriphale on 2006-01-08
to skip any services on startup, just hit Ctrl+C when that service is being started.

Once you have started up, and there is a network connection, if it is not automatically connected, got to System->Administration->Networking
Enter your password, select your network connection and hit the "Activate" button.

---

