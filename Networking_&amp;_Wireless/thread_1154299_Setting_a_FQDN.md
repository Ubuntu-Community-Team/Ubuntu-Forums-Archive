---
title: "Setting a FQDN?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2009-05-09
I know this has been asked a million times, but I have yet to find any good way to do it despite many google searches.

I need to set a system-wide FQDN (mostly for apache), using the following info:
Hostname: USSR-MOSCOW
Website: <no, sorry>.dyndns.org.

Can anybody give me some help with /etc/hosts? I'm at my wits end. :(

---

### Post by albinootje on 2009-05-09
> **rhcm123 said:**
>  Can anybody give me some help with /etc/hosts?

You'll be wanting to edit /etc/hostname instead.
See also "man hostname", to test with the command "hostname".

---

### Post by rhcm123 on 2009-05-09
> **albinootje said:**
> You'll be wanting to edit /etc/hostname instead.
See also "man hostname", to test with the command "hostname".

according to man hostname, i need to be editing /etc/hosts 

>        You can’t change the FQDN (as returned by hostname --fqdn) or the DNS domain name (as  returned
       by  dnsdomainname)  with  this command. The FQDN of the system is the name that the resolver(3)
       returns for the host name.

       Technically: The FQDN is the name gethostbyname(2) returns for the host name returned by  geth&#8208;
       ostname(2).  The DNS domain name is the part after the first dot.

       Therefore  it  depends  on the configuration (usually in /etc/host.conf) how you can change it.
       Usually (if the hosts file is parsed before DNS or NIS) you can change it in /etc/hosts.


From what ive read, the FQDN is whatever the resolving system sets it as. In ubuntu (see /etc/host.conf) it defaults to /etc/hosts, then BIND.

I need to know what lines i put into /etc/hosts to set a system wide FQDN.

---

### Post by albinootje on 2009-05-09
> **rhcm123 said:**
> according to man hostname, i need to be editing /etc/hosts 


Well, I speak from experience, but try it yourself :

1) edit /etc/hostname, to e.g. yourhost.dyndns.org
2) run : hostname -F  /etc/hostname
3) edit /etc/hosts accordingly
4) /etc/init.d/apache2 restart

Some applications might need time to get used to the change, a reboot would be handy imho.

---

### Post by capscrew on 2009-05-09
> **rhcm123 said:**
> according to man hostname, i need to be editing /etc/hosts 



From what ive read, the FQDN is whatever the resolving system sets it as. In ubuntu (see /etc/host.conf) it defaults to /etc/hosts, then BIND.

I need to know what lines i put into /etc/hosts to set a system wide FQDN.

The /etc/hosts file is normally for the localhost (the machine the file resides on).  If you want to use an /etc/hosts file for domain wide (LAN) you can use DNSmasq.  This uses the local /etc/hosts file for domain wide name resolution.  The term FQDN typically denotes a hostname.domainname listing.

---

### Post by albinootje on 2009-05-09
In my previous comment I've put step 3 there, but I just tested this with only steps 1, 2 and 4, and apache clearly responded to the changes.

---

### Post by rhcm123 on 2009-05-09
> **capscrew said:**
> The /etc/hosts file is normally for the localhost (the machine the file resides on).  If you want to use an /etc/hosts file for domain wide (LAN) you can use DNSmasq.  This uses the local /etc/hosts file for domain wide name resolution.  The term FQDN typically denotes a hostname.domainname listing.

That's a helpful/good idear, as this system is also the localnetwork DHCP server. Can you give me some helpful starter tips on how to do use DNSmasq?

---

### Post by rhcm123 on 2009-05-09
> **albinootje said:**
> In my previous comment I've put step 3 there, but I just tested this with only steps 1, 2 and 4, and apache clearly responded to the changes.

Did that, got this output from restarting apache:
```

apache2: apr_sockaddr_info_get() failed for USSR-MOSCOW.<wat>.dyndns.org
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
 ... waiting .apache2: apr_sockaddr_info_get() failed for USSR-MOSCOW.<wat>.dyndns.org
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                               
```

---

### Post by capscrew on 2009-05-09
> **rhcm123 said:**
> That's a helpful/good idear, as this system is also the localnetwork DHCP server. Can you give me some helpful starter tips on how to do use DNSmasq?

There's not much to say.  It is a lightweight DHCP/DNS server for local networks.  It will act as a DNS forwarder for Internet DNS requests.  In addition it will handle dynamic mapping for hostnames to DHCP IP addresses.

The main page for DNSmasq is [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/doc.html**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/doc.html")

All the documentation is located at [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/docs/**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/docs/")

Read the man page all the way through and very carefully. It is available at: [[COLOR="Blue"]**http://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html**[/COLOR]]("http://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html")

Edit: And of course there is Wikipedia's write up at: [[COLOR="Blue"]**http://en.wikipedia.org/wiki/Dnsmasq**[/COLOR]]("http://en.wikipedia.org/wiki/Dnsmasq")

---

### Post by SirGe on 2010-04-03
I have a solution, that works for me; if it works for you, use it.

There are two files, that control how names are looked up: */etc/host.conf* and */etc/nsswitch.conf*. As far as I can tell, *host.conf* is old technology, superseded by *nsswitch.conf*. I do not know whether use of *nsswitch.conf* is hardwired, or *host.conf* is used as a fallback when *nsswitch.conf* is not present.

My /etc/host.conf has ```
order hosts,bind
```, which means */etc/hosts* is searched first, then DNS.

My *nsswitch.conf* has 
```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
which results in the same behavior: files, than DNS.

Does not matter: we leave both as is.

My */etc/hosts* has two relevant lines:
```

127.0.0.1 localhost
127.0.0.1 my-hostname

```

And, of course, */etc/hostname* has *my-hostname*.

So, because files are hit first, ```
hostname --fqdn
``` cannot get a FQDN, it only gets a short name. And Apache whines.

One way to try to fix this is to replace *my-hostname* in */etc/hosts* with FQDN. This makes Apache happy, but lookups for *my-hostname* are broken (unless DNS knows how to resolve them) and lookups for FQDN (e.g. *my-hostname.my-domain.net*)return 127.0.0.1, which sucks.

You can add *my-hostname* on the same line with the FQDN. If you add it before the FQDN, the FQDN is not seen and Apache whines again. If you add it after the FQDN, things are OK, but both the hostname and the FQDN are resolved to 127.0.0.1 - gack!

The right thing is to have both the short name and the FQDN resolve to the real IP address.

If you do not have a functional DNS server on your network and your IP is static, just put the line with
```

123.45.67.89 my-host.my-domain.net my-host

```
in */etc/hosts* (substitute real IP address/names).

If you do not have a functional DNS server and your IP is dynamic, go hack your DHCP scripts, so this gets fixed when your IP address changes. But in this case I suspect you are not running an Apache server, that can be accessed from outside your machine.

If you have a DNS server, then just comment out the line in */etc/hosts*, so that the names - both short and long - are resolved via DNS. 

This does the right thing for *hostname*, *hostname --fqdn*, Apache, etc. for short name, FQDN and localhost.

---

