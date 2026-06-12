---
title: "Samba max connections problem"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-03-01
Hello,
we use Samba to serve about 70 Win2k/XP clients. For a few days now, we suddenly have a problem that newly created user can't log in to the Samba domain, although already existing users work fine. When I try loggin in with a newly created username on a machine, it tells me that our domain is not available. Sometimes after a few login attempts it suddenly works.

When I log in to any computer as (local) administrator and do a "net view samba-server" it tells me that it "can't establish a connection to the remote computer because the maximum number of clients is connected to this computer".

Right now about 50% of our staff is here, so this is kind of a strange message. The server is absolutley capable of serving much more users (it's a quad Xeon machine), but it run's a whole lot of smbd processes (~1000, yes, ONE THOUSAND)

Any ideas what could be wrong here?

Tom

---

