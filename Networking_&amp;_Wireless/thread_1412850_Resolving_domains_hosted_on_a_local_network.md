---
title: "Resolving domains hosted on a local network"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by esauer on 2010-02-21
I am running an ubuntu web server that is hosting several domain names. However, I cannot get any machines that are on the same router as the server to resolve the global ip or domain names on pointing to the server. What can I do to change this? I know I could edit my hosts file, however, I would like this to work on my ubuntu laptop, which is often taken to other networks.

---

### Post by dmizer on 2010-02-21
> **esauer said:**
> I am running an ubuntu web server that is hosting several domain names. However, I cannot get any machines that are on the same router as the server to resolve the global ip or domain names on pointing to the server. What can I do to change this? I know I could edit my hosts file, however, I would like this to work on my ubuntu laptop, which is often taken to other networks.

Your best and easiest answer is the hosts file.

Otherwise, you'll need to add a local DNS server. This DNS server should not be hosted on the same machine as your web server.

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

---

### Post by R.Bucky on 2010-02-21
Why wouldn't you have DNS on the same box as web services? That seems counter-intuitive.

Depending on how you are pushing your content, CMS or static pages, you would surely need Bind or other DNS internally. I had the same problem with a dozen or so domains where managing with hosts file is impractical, not to mention bad practice.

---

### Post by dmizer on 2010-02-21
How is managing name resolution considered bad practice in a small LAN situation described by the OP?

In my opinion, the less LAN resources you have running on servers facing the internet, the better.

---

