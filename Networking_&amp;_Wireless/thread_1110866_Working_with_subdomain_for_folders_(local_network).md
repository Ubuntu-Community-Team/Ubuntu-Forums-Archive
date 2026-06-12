---
title: "Working with subdomain for folders (local network)"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by riotbr on 2009-03-30
First of all, sorry about my english.

Well... I have found a lot of good info about setting what I need here but without success.

My network: an ADSL router (10.1.1.1), a hub, a workstation (XP - 10.1.1.3) and my server running Apache2.2+PHP+MySQL (Ubuntu Desktop 8.04 - 10.1.1.4 - act like a web and file server).

What I want it's only to local access and for development purposes: to set subdomains pointing to folders in my document root.

So, assuming that my (fake and local) domain is "www.intranet.inc", what I want is when accessing this URL I see all the folders in the root, and when accessing "project01.intranet.inc" I see/run the content of the folder "project01" on the root. I need this accessing from the workstation and the server.

I tried do this with BIND9 + virtualhosts on Apache2.2 but the result wasn't what I want (only access the document root).

Guys (and girls) I lost 3 days in a LOT of documents and tutorials. Any help will be welcome.

[]'s from Brazil.

Eduardo

---

### Post by riotbr on 2009-03-30
Sorry about the bump but I really need some help for this.

In advance: for each virtualhost created on Apache I need too insert a new entry on the BIND for the subdomain?

Thanks,
Eduardo

---

