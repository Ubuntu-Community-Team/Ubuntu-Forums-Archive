---
title: "DNS not working as expected"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by cpressland on 2010-11-22
Hey Guys wassup?

Our Active Directory server is also our primary DNS Server, located at 192.168.20.2 which forwards to 208.67.222.222 & 208.67.220.220 but obviously it also handles internal hosts, so on Windows if I type [http://intranet/](http://intranet/) into a web browser, it'll talk to 20.2 and ask for 'intranet' which is 192.168.20.23, then it'll jump to the relevant page as expected.

This isn't working on Ubuntu, I've configured 'NetworkManager' and checked the settings are in /etc/resolv.conf
'Nameserver 192.168.20.2'

However when I type say, 'ping intranet' I get a host not found, but obviously if I type the IP it works fine.

Any ideas on where the issue is?

Thanks

Chris

EDIT:

Output of nslookup:

```
cpressland@mint-vm /etc $ nslookup intranet
Server:         192.168.20.2
Address:        192.168.20.2#53

** server can't find intranet: SERVFAIL
```

---

### Post by SeijiSensei on 2010-11-22
The DHCP server isn't sending the domain name to the clients when they boot up.  Without a "domain example.com" or "search example.com" entry in resolv.conf, an "unqualifed" host name like "barney" won't resolve because the DNS server is looking for "barney.example.com".

There are a couple of solutions to this.  The best one is to fix the DHCP server configuration (on the AD server, I'd suspect) to send the domain.  Failing that, you can use the "prepend" directive in /etc/dhcp3/dhclient.conf to add a "domain example.com" line to the top of resolv.conf.

---

### Post by cpressland on 2010-11-22
Not sure I follow, none of our servers have a 'dot com' address... So where does this example.com come into it?

---

### Post by cpressland on 2010-11-22
Nevermind, fixed that.

---

