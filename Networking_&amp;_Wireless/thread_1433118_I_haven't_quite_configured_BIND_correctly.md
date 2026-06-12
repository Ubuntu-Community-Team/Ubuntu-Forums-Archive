---
title: "I haven't quite configured BIND correctly"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by BigRichOfYork on 2010-03-18
I have set up BIND on my Ubuntu 9.04 development server in order to use XAMP and VHCS2. The online documentation has been very helpful but I must be missing something.

I think I have a problem with BIND, because when I try to resolve local names e.g. www for my domain it fails to resolve (a). If I put in the FQDN it also fails to resolve and in the error message it appears to duplicate the domain name (b) e.g. in nslookup:

(a)
> www

Server:        10.10.7.16
Address:    10.10.7.16#53

** server can't find www: NXDOMAIN

(b)
> [www.testdomain.co.uk]("http://www.testdomain.co.uk")

Server:        10.10.7.16
Address:    10.10.7.16#53

** server can't find [www.testdomain.co.uk.testdomain.co.uk:]("http://www.testdomain.co.uk.testdomain.co.uk:") SERVFAIL

In my hosts file (and I'm not convinced I'm correct here) I have:

# 'hosts' file configuration.

127.0.0.1    TestServer.localdomain localhost
10.10.7.16    TestServer.testdomain.co.uk TestServer

In my hostname file I just have:

TestServer

And in resolv.conf I have:

search testdomain.co.uk
nameserver 10.10.7.16


I know that BIND is working because it successfully forwards and resolves queries for other domains. The main problem is that it appears to be preventing VHCS2 from enabling a domain for me to work with.

Any suggestions please?

---

### Post by jrssystemsnet on 2010-03-18
> **BigRichOfYork said:**
> I know that BIND is working because it successfully forwards and resolves queries for other domains. The main problem is that it appears to be preventing VHCS2 from enabling a domain for me to work with.

Any suggestions please?Bind does not refer to the local hosts file; bind only works with zone files.

This is a sample zone reference which would go in /etc/bind/named.conf.local:

```
zone "masterdomain.net" {
        type master;
        file "zones/masterdomain.net";
};
```

And then this file would go in /etc/bind/zones/masterdomain.net:

```
$ORIGIN net.
$TTL 5m

masterdomain    IN     SOA    www.masterdomain.net. hostmaster.www.masterdomain.net. (
                                  1               ; serial
                                  4h              ; refresh
                                  15m             ; retry
                                  8h              ; expire
                                  4m)             ; negative caching TTL
                IN      NS      ns1.masterdomain.net.
                IN      NS      ns2.masterdomain.net.
                IN      MX      10 mail.masterdomain.net.
                IN      A       68.96.111.12

$ORIGIN masterdomain.net.
www             IN      CNAME   masterdomain.net.
ns1             IN      A       68.96.111.10
ns2             IN      A       68.96.111.11
```

You'll need to do an **/etc/init.d/bind9 restart** after adding a zone, then you test it using the **dig** command.  Assuming you're shelled into the server running bind, the format would look like this:

```
you@dnsbox:~$ dig @127.0.0.1 masterdomain.net
```

Hope this helps.

---

### Post by doas777 on 2010-03-18
I do this by configuring the clients with a "search" domain in /etc/resolv.conf
just by adding a line like:
```

search domain.tld

```edit: ahh I see you know that trick. and that your problem is a little more serious. need to read better...

have you verified your zone with 
named-checkzone <domain> <zonefilepath>

---

### Post by BigRichOfYork on 2010-03-19
Thanks for the info, I should have made clear in my orignal post that I have set up the zone files (forward and reverse) and restarted the daemon. The reason I was focusing on the host files is that it doesn't seem to be searching based on the domain membership of the local machine and when I put in the FQDN it then tags the domain name onto the end of that.

I do have the search line in my resolv.conf too, which is why I'm so confused.

My main experience of DNS to date is with Microsoft (sorry!) Active Directory so maybe I'm expecting it to behave in the wrong way?

Best regards

-Rich

---

### Post by jrssystemsnet on 2010-03-19
> **BigRichOfYork said:**
> when I put in the FQDN it then tags the domain name onto the end of that

That's because you have the "search domain" option in your /etc/resolv.conf - so if ANY address comes up NXDOMAIN, it tries again with thataddress.testdomain.co.uk.

Again, you need to stop poking at the host file and concentrate on BIND.  The host file has absolutely NOTHING to do with BIND, and will not influence the way BIND answers DNS queries in any way.  Just like Microsoft, the hosts file is ONLY used by the local machine for its own benefit.

Also don't use nslookup - it's been deprecated for years.

Show us the named.conf file, the zone file for testdomain.co.uk, and the output of **dig @127.0.0.1 testdomain.co.uk**, and then maybe we can get somewhere.

---

### Post by BigRichOfYork on 2010-03-22
Here are all the BIND related files and the output from dig @ 127.0.0.1

I noticed that when I restarted the BIND daemon that it warns me I can't resolve the name of the server (FDSC02).

File rev.7.10.10.in-addr.arpa

@ IN SOA ns1.testdomain.co.uk. admin.testdomain.co.uk (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.testdomain.co.uk.
16                   IN    PTR    testdomain.co.uk


File testdomain.co.uk.db

testdomain.co.uk.      IN      SOA     fdsc02.testdomain.co.uk. admin.testdomain.co.uk. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

testdomain.co.uk.      IN      NS              fdsc02.testdomain.co.uk.
testdomain.co.uk.      IN      MX     10       mail.testdomain.co.uk.

www              IN      A       10.10.7.16
mail             IN      A       10.10.7.16
fdsc02           IN      A       10.10.7.16


File named.conf.local

zone "testdomain.co.uk" {
        type master;
        file "/etc/bind/zones/testdomain.co.uk.db";
        };

zone "0.10.10.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.7.10.10.in-addr.arpa";
};


File resolv.conf

nameserver 10.10.7.16


Ouput from dig @127.0.0.1

; <<>> DiG 9.5.1-P2.1 <<>> @127.0.0.1
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 27589
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 11

;; QUESTION SECTION:
;.                IN    NS

;; ANSWER SECTION:
.            76951    IN    NS    j.root-servers.net.
.            76951    IN    NS    e.root-servers.net.
.            76951    IN    NS    c.root-servers.net.
.            76951    IN    NS    m.root-servers.net.
.            76951    IN    NS    b.root-servers.net.
.            76951    IN    NS    g.root-servers.net.
.            76951    IN    NS    k.root-servers.net.
.            76951    IN    NS    d.root-servers.net.
.            76951    IN    NS    h.root-servers.net.
.            76951    IN    NS    i.root-servers.net.
.            76951    IN    NS    f.root-servers.net.
.            76951    IN    NS    a.root-servers.net.
.            76951    IN    NS    l.root-servers.net.

;; ADDITIONAL SECTION:
a.root-servers.net.    76951    IN    A    198.41.0.4
b.root-servers.net.    76951    IN    A    192.228.79.201
c.root-servers.net.    76951    IN    A    192.33.4.12
d.root-servers.net.    76951    IN    A    128.8.10.90
e.root-servers.net.    76951    IN    A    192.203.230.10
f.root-servers.net.    76951    IN    A    192.5.5.241
g.root-servers.net.    76951    IN    A    192.112.36.4
h.root-servers.net.    76951    IN    A    128.63.2.53
i.root-servers.net.    76951    IN    A    192.36.148.17
j.root-servers.net.    76951    IN    A    192.58.128.30
k.root-servers.net.    76164    IN    A    193.0.14.129

;; Query time: 4 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Mar 22 16:15:13 2010
;; MSG SIZE  rcvd: 404
;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Mar 22 16:09:38 2010
;; MSG SIZE  rcvd: 404

---

### Post by BigRichOfYork on 2010-03-26
I gave in to temptation and installed G-Adim BIND last night, and it immediately found some problems with my configuration. However, I now can't restart the BIND daemon.

I have found threads with a similar problem - unable to open etc/named.conf which relates to file permissions, however, all the permissions appear to be correct.

Can any one point me to some good documentation on using G-Admin BIND?

Thanks

---

