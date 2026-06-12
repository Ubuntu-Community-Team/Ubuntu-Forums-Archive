---
title: "BIND9 DNS doesnt work externally?"
date: 2013-07-11
forum: Networking &amp; Wireless
---

### Post by altirisx on 2013-07-11
I have BIND9 installed on an ubuntu distro, I have configured it and created forward/reverse zones etc. Currently I can run the command nslookup on my hostname, domain name, mail server, ftp etc.  and all of it gets resolved (mail.domainname.com, ftp.domainname.com etc). However if I go to one of my other computers (windows server) on the network it can ping the hostname and it sends connections however it cant do nslookup the hostname or domainname. I DO NOT have the domain name purchased and registered with my ISP yet, is this why it doesnt work externally? Do I by any chance need to make something like an A record for the external IP address on the zone files?

Here are my zone files for you guys, I replaced my actual domain with domain/domainname   the same goes for my hostname, I replaced it with hostname.

**Forward Zone**
```
$ORIGIN domain.com.
$TTL 86400
@    IN    SOA    dns1.domain.com. hostmaster.domain.com. (
    2013071101 ;serial
    21600        ;refresh after 6 hours
    3600       ;retry after 1 hour
    604800     ;expire after1 week
    86400 )    ;minimum TTL 1 day

    IN    NS     dns1.domain.com.
    
    IN    MX    10    mail.domain.com.

    IN    A    192.168.12.137

dns1    IN    A    192.168.12.137

hostname    IN    A    192.168.12.137

ftp    IN    A    192.168.12.137

mail    IN    CNAME    hostname

www    IN    CNAME    hostname

```

**Reverse Zone**
```
$ORIGIN 12.168.192.in-addr.arpa.
$TTL 86400
@    INandre-server    SOA    dns1.domain.com. hostmaster.domain.com. (
    2013071101 ;serial
    21600       ;refresh after 6 hours
    3600       ;retry after 1 hour
    604800     ;expire after1 week
    86400 )    ;minimum TTL 1 day

@    IN    NS     hostname.domain.com.
    
1    IN    PTR    hostname.domain.com.

2    IN    PTR    hostname.domain.com.

3    IN    PTR    hostname.domain.com.

4    IN    PTR    hostname.domain.com.


```

---

### Post by newbie-user on 2013-07-12
Yes, you will need to purchase a domain name first before your domain can resolve externally.

---

### Post by altirisx on 2013-07-12
Alright sweet that's fine, so I DONT need to add some type of record for my external IP or do I need to do that too?

---

### Post by newbie-user on 2013-07-12
If you are hosting services from your external IP, you do need some A records pointing to your external IP so that those services can be resolved externally. Even if you aren't hosting services from your external IP, you would still need some records pointing to wherever those services are located.

---

