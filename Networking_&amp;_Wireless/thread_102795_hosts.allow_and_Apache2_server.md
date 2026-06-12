---
title: "hosts.allow and Apache2 server"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by hansonlee on 2005-12-12
Hi I am wondering if I can use /etc/hosts.allow file regulate the incoming traffic requresting http service?

I tried adding "ALL : ALL : deny" command in /etc/hosts.allow, but other computers can still access to the http content, even after purging all the internet caches.

This method does block the SSH service, though, so it is actually working in some respect.

---

