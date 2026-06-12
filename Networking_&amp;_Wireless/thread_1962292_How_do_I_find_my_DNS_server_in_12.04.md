---
title: "How do I find my DNS server in 12.04?"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by lethalfang on 2012-04-20
DNS server used to be contained in the file /etc/resolv.conf.
Well, no longer the case in 12.04. The file /etc/resolv.conf shows 127.0.0.1.

---

### Post by newbie-user on 2012-04-21
On one of my 12.04 machines, I found it in /etc/resolvconf/resolv.conf.d/original, but the other 12.04 didn't have that file.

---

### Post by lethalfang on 2012-04-21
> **newbie-user said:**
> On one of my 12.04 machines, I found it in /etc/resolvconf/resolv.conf.d/original, but the other 12.04 didn't have that file.

I'm guessing you upgraded from a previous version, which handled things differently, and that's how the "original" file got there. 
On newly installed 12.04, I can't find the "nameserver" information anywhere.

---

### Post by newbie-user on 2012-04-21
Actually they were both fresh installs, so I don't really understand that. Although, one of the computers used 12.04 beta 1.

Anyway, you can also check DNS servers in /run/nm-dns-dnsmasq.conf

---

### Post by lethalfang on 2012-04-22
> **newbie-user said:**
> Actually they were both fresh installs, so I don't really understand that. Although, one of the computers used 12.04 beta 1.

Anyway, you can also check DNS servers in /run/nm-dns-dnsmasq.conf

Yeah, there they are. 
I need to know my DNS because I set up my computer as a VPN server, and I push the DNS into the clients. 
They must've changed how to handle the DNS thing between beta1 and beta2....

---

### Post by jdthood on 2012-11-05
As of Ubuntu 12.10 you can't see the nameserver address(es) given to the local forwarding nameserver in /run/nm-dns-dnsmasq.conf any more. Instead you can do

    nmcli -f IP4 dev list | grep DNS

Ref: [http://askubuntu.com/questions/180094/is-there-a-way-to-make-dig-report-the-actual-name-server-rather-than-127-0-0-1](http://askubuntu.com/questions/180094/is-there-a-way-to-make-dig-report-the-actual-name-server-rather-than-127-0-0-1)

---

### Post by pqwoerituytrueiwoq on 2012-11-05
you mark a thread as solved from the thread tools menu (under replay to the right at the top of the page)
this is another way
```
nm-tool | grep DNS
```

---

