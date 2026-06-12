---
title: "nginx +vhosts without public IP"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by dom2 on 2012-07-15
Hello,

I've got server for my friends, all works fine but they asked if they could have ~/www.

I've installed nginx with php5-cgi for official www of the server.

Normally I'd create vhosts, but how can I do that without public IP, so I could have user.no-ip.domain or no-ip.domain/~user ?

thank you for any suggestions!

---

### Post by Kirk Schnable on 2012-07-16
Sure.  As long as you have a DNS of some sort pointing to your server's IP, it doesn't matter what type of DNS it is, you can setup a vhost and restart nginx, and it should load right up correctly.

You could have user1.no-ip.org and user2.no-ip.org as separate vhosts.  Because if I remember correctly. No-IP free doesn't support subdomains (user1.user2.no-ip.org).

Kirk

---

