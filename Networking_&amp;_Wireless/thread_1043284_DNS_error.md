---
title: "DNS error"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by saecheong89 on 2009-01-18
Hi people!
I am new to ubuntu here.
Currently using 8.0.4

I am 3 machines running.
1. Ubuntu 8.0.4 server
2. Windows XP professional
3. Windows 2003 server

My windows xp has no problem running nslookup (dns by host name and reverse dns by ip address) in ubuntu server. however my windows 2003 server is unable to do nslookup (name of host) but is able to do reverse nslookup using ip address.

Any idea what went wrong?

---

### Post by Macchi on 2009-01-18
Personally I prefer to set a local split-DNS server in the network, but it takes some time...

A quick hack is to add the IP addresses (static) and host names to the /etc/hosts on the three machines, yes even on Win. Google for /etc/hosts on Win.
Keep in touch.

---

### Post by capscrew on 2009-01-18
I believe the file Macchi is referring to is:```
C:\Windows\system32\drivers\etc\hosts
```

---

### Post by saecheong89 on 2009-01-19
hey..thank you for all the reply.
i think something went wrong with the network interface.
i attempted again today, and it went well already =) 
THANK YOU!!

---

