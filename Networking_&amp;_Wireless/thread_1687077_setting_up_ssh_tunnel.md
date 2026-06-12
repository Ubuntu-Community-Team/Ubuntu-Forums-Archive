---
title: "setting up ssh tunnel"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by Choad on 2011-02-13
i'm trying to set up a tunnel so that <local_machine> routes all traffic on <port> through <remote_machine> in the hope that externally it will appear as though connections made from <local_machine> are originating from <remote_machine>

is the command 

ssh -D <port> -fN user@<remote_machine>

the correct command for this?

---

