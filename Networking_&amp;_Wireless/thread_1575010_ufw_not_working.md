---
title: "ufw not working?"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by AZzKikR on 2010-09-15
I've got an Ubuntu server box, which frequently gets some SSH brute-force attacks. Occasionally when I check my auth.log and see that a certain IP did a crapload of attacks, I just add a firewall rule:

```
$ sudo ufw deny proto any from $IP
```

After a check if it's loaded into ufw:

```
$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
22/tcp                     LIMIT   Anywhere
21/tcp                     LIMIT   Anywhere
22/tcp                     ALLOW   192.168.1.0/24
Anywhere                   DENY    $IP

```

Of course, $IP should be substituted with the IP I'm trying to block. Now, after checking auth.log a day or two later, I still see break-in attempts from that very IP. I don't get it. Can anyone shed some light on this?

Thanks.

---

