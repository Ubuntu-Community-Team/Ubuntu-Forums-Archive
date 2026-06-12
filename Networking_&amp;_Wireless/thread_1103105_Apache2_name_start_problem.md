---
title: "Apache2 name start problem"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-03-22
Hi all after installing ISPConfig 3.0.0.9 rc2 I get this problem.

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


I am on Ubuntu 8.04.

What can I do to resolve this.

Thanks.

---

### Post by jjross on 2009-03-22
This just means that you dont have a domain name specified in your apache2 configuration, it is telling you it is using 127.0.0.0 instead.
Its not that big of a problem, it will still start and run apache2.
You can search this forum and find more references to this error.

---

