---
title: "Configuring SQUID in Ubuntu 9.10"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by linuxrockers on 2010-01-27
How to configure SQUID proxy server in ubuntu 9.10 ? I am a newbie of SQUID!

---

### Post by Shaker242 on 2010-01-27
I'd start here: [SQUID]("http://www.lmgtfy.com/?q=squid+setup+ubuntu+9.10")

---

### Post by Lars Noodén on 2010-01-27
> **linuxrockers said:**
> How to configure SQUID proxy server in ubuntu 9.10 ? I am a newbie of SQUID!

Try the [Ubuntu Community Squid guide](https://help.ubuntu.com/community/Squid).  There's an error in the guide, you do not need apache for squid.  The only trick is part of installing squid is the configuration, as you have noted, and usually the only trick there is to set the ACL to allow access.  Open squid.conf with your favorite editor (using sudo) and then find the lines with the string **http_access** as mentioned in the guide.  Walk through that part line by line.

---

