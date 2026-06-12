---
title: "Strange issue with internet connectivity"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by DarkSnake on 2010-04-15
Okay, so I'm running Ubuntu 9.10, and I have a LAMP setup.

The server connects fine, I can load pages, FTP in, etc. So everything seems good on that end.

When I try to use the internet from the Ubuntu box, however, it doesn't seem to want to connect. The internet won't load through firefox, and attempting to update through the repository won't connect.

I've tried playing around with refreshing the connection and rebooting and such, but nothing seems to be fixing this. I can't think of what the issue may be as the connection is working, as I can get on the server, but can't seem to get it to connect outward from the actual box.

---

### Post by Iowan on 2010-04-15
Do both machines have a common connection to a router/modem/etc, or is the server between the internet and the other machine?

---

### Post by DarkSnake on 2010-04-15
Both the machines I'm on now are on the same router, but I also tested it from campus and the server aspect was working fine.

---

### Post by renkinjutsu on 2010-04-16
Can your server ping hostnames?
```
ping google.com
``` or can it only ping IP's?
```
ping 74.125.95.106
```

---

### Post by DarkSnake on 2010-04-16
Hmm, it seems to actually work with google's IP when pinging (and accessed the site via the IP successfully). Must be a DNS issue then, any idea on how to fix it?

---

### Post by DarkSnake on 2010-04-16
Got it running, just changed the DNS to google's public one. Thanks for the help.

---

