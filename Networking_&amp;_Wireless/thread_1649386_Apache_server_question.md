---
title: "Apache server question"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by johnmay on 2010-12-20
I have a web site that logs ip addresses and I have a system on my local network which hits the web site every three or four seconds. Is there a  setting I can change on my server to minimize that? The 'offending' computer is not under my administration. 

Thanks

---

### Post by robert_pectol on 2010-12-20
You could just block access from the offending IP.  Open a shell on the server and type:
```

sudo iptables -I INPUT -p tcp -s <offending_IP> --dport 80 -j DROP

```

---

### Post by johnmay on 2010-12-20
Thanks!

---

### Post by Choragos on 2011-01-04
This is a bit of a hijack, but it's along the same lines and the question was answered, so here goes.

I have been using IP tables to block particular IP addresses, so I thought.  Then I looked at what the rules are, and it's only saving my last entry (I think).  I have been using this to block:

```

iptables -A INPUT -s xxx.xxx.xxx.xxx -j DROP

```Upon running
```
iptables -L -n
``` at the end of the INPUT chain I see:
```

DROP       all  --  xxx.xxx.xxx.xxx       0.0.0.0/0           

```where the IP address is the last one I blocked.  Am I doing something incorrectly?  What's the difference between -A and -I?   I read the manpage and didn't see what should have been a big difference.  I specifically am blocking IP addresses that are attempting to ssh in as root (any brute force attack), but I have no problem generally blocking them from any port.

Thanks so much.

---

