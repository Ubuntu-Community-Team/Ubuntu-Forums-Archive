---
title: "Turn off SSH"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by warnesey333 on 2008-12-24
Hi, 
I'm looking for a way to turn on and off SSH remotely on my webserver.

An idea i've had:
PHP script that is in a username/password protected folder on /var/www/
However - can't seem to get it to to turn it on due to permissions

If anyone can help me along with the permissions error or suggest a different idea!

Would be extremely grateful

Thanks

---

### Post by kevdog on 2008-12-24
Keep the ssh daemon running all times, but mask with firewall that keeps it port closed.  Run a port knocker utility such as fwknop that would temporarily open a hole in your firewall that would allow external access.

---

