---
title: "Can't resolve local dns names using Windows dns server?"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by ingramproductions on 2010-11-20
I have a Windows Server 2008 on my network functioning as dns server. All systems use this server to resolve names. They resolve both local network and internet names from it. It is also a domain controller. Windows systems that are joined to the domain, as well as Windows systems that are not joined to the domain can resolve names.

My Ubuntu 10.10 system will not resolve names on the local network, but it will resolve internet names.

Any idea on how to get my system to resolve these names?

---

### Post by SeijiSensei on 2010-11-20
Are you talking about "fully-qualified" domain names like "host.example.com" or unqualified names like "host"?  If the latter, take a look at /etc/resolv.conf.  Does it have a "domain" or a "search" directive followed by the domain?  If not, your DHCP server is probably not sending the domain name to the clients.  Either you can create a static resolv.conf with the domain hard-coded like this:

```

domain example.com
nameserver 4.4.4.4
nameserver 8.8.8.8

```

replacing the addresses above with the DNS servers on your network (those are Google's DNS servers), or you can configure DHCP to send the domain.  You can also pick and choose which pieces of information you want to obtain via DHCP by editing /etc/dhcp3/dhclient.conf.

---

### Post by SeijiSensei on 2010-11-20
double-post because of server delays deleted

---

### Post by ingramproductions on 2010-11-20
Thank you very much. That was exactly the problem.

---

