---
title: "mail times"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by eatloaf on 2009-04-27
I did a clean install of 9.04 and sending a mail now takes about a minute. Specifically, after the Ctrl-D, or after the mail executes, it takes a minute (!!) to get the prompt back. I've never seen this in 8.x.

Any ideas?

---

### Post by eatloaf on 2009-04-29
Not having the longname of my machine in /etc/hosts was causing sendmail to stall.

/etc/hosts should contain:

ipaddress longname shortname

eg:
27.0.0.1 mycomputer.local mycomputer



Now it's zippy again.

---

