---
title: "Apache can't connect from outside"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by musashi39 on 2010-07-21
I can't connect to apache from outside the LAN. I can connect to everything else (ssh ftp) from outside.

I'm getting Error 101 (net::ERR_CONNECTION_RESET): Unknown error

My router is configured to redirect port 80 to my webserver. I am getting access logs etc and error logs for missing files (favicon)

---

### Post by musashi39 on 2010-07-21
I feel like a complete idiot. I just checked every last setting in my router and I had remote management set to port 80..... oops.

---

