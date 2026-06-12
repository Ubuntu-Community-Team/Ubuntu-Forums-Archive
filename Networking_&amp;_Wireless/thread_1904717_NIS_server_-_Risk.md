---
title: "NIS server - Risk"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by achuth on 2012-01-05
Sir,
I have 50 networked computers.
One of those machines is a server class machine.
I wish to implement NIS & NFS based login to all 49 clients.
Based on my reading so far, I learned that ..if the server fails then the clients cannot login.
My doubt is whether I can keep two accounts at the client computers, one to login to the NIS server, and an other normal user account which do not use the NIS Server.

If that is possible, then if the server fails, I can still login in the client machines usng the secondary account in case of emergency. Is it possible to have a secondary account which do not require an NIS server to be up?

---

### Post by bab1 on 2012-01-05
> **achuth said:**
> Sir,
I have 50 networked computers.
One of those machines is a server class machine.
I wish to implement NIS & NFS based login to all 49 clients.
Based on my reading so far, I learned that ..if the server fails then the clients cannot login.
My doubt is whether I can keep two accounts at the client computers, one to login to the NIS server, and an other normal user account which do not use the NIS Server.

If that is possible, then if the server fails, I can still login in the client machines usng the secondary account in case of emergency. Is it possible to have a secondary account which do not require an NIS server to be up?

Sure you can a local account to log into a client when NIS is down, but it is a different account. The NIS account is a "global account".  It's good practice to make a "local" account on each client machine.  Do not use the same login for the local account.  I use first name for the local account and first initial + last name for the global account.

As the local user is really for emergencies only you can keep a simple home directory that does not need an NFS mounted home directory.

---

