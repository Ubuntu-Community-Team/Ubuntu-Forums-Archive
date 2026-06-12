---
title: "Configuring BIND 9"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by bluedalmatian on 2009-02-24
Im trying to setup a single BIND 9 DNS server on our (isolated) LAN for the domain xswitch.local
The primary DNS server will be comet.xswitch.local (192.168.254.200)

Ive got BIND running and the config file seems OK. 

Ive edited /etc/resolv.conf to point to 192.168.254.200 but when I type host comet.xswitch.local at the command line I get 'error 2 SERVFAIL' so I guess it must be a problem with the zone files?

The 3 zone files are as follows:

-------------------------------------
--/var/named/db.xswitch.local below--
-------------------------------------
$TTL 3h
xswitch.local. IN SOA comet.xswitch.local. (
	1	;serial
	3h	;Refresh after 3 hours
	1h	;Retry after 1 hour
	1w	; exp after 1 week
	1h)	;

xswitch.local. IN NS comet.xswitch.local.

localhost.xswitch.local. IN A 127.0.0.1
comet.xswitch.local. IN A 192.168.254.200
cupid.xswitch.local. IN A 192.168.254.201
dancer.xswitch.local. IN A 192.168.254.202
sip.xswitch.local. IN A 192.168.254.201
sip.xswitch.local. IN A 192.168.254.202





-------------------------------------
--/var/named/db.192.168.254 below--
-------------------------------------

254.168.192.in-addr.arpa. IN SOA comet.xswitch.local. (
	1	;serial
	3h	;Refresh after 3 hours
	1h	;Retry after 1 hour
	1w	; exp after 1 week
	1h)	;

xswitch.local. IN NS comet.xswitch.local.


200.254.168.192.in-addr.arpa. IN PTR comet.xswitch.local. 
201.254.168.192.in-addr.arpa. IN PTR cupid.xswitch.local.
202.254.168.192.in-addr.arpa. IN PTR dancer.xswitch.local. 
201.254.168.192.in-addr.arpa. IN PTR sip.xswitch.local.
202.254.168.192.in-addr.arpa. IN PTR sip.xswitch.local.
-------------------------------------



-------------------------------------
--/var/named/db.127.0.0 below--
-------------------------------------
0.0.127.in-addr.arpa. IN SOA comet.xswitch.local. (
	1	;serial
	3h	;Refresh after 3 hours
	1h	;Retry after 1 hour
	1w	; exp after 1 week
	1h)	;

0.0.127.in-addr.arpa. IN NS comet.xswitch.local.

1.0.0.127.in-addr.arpa. IN PTR localhost.


Im sure Im overlooking something very simple here id be grateful if anyone can spot what it is?

Thanks

---

### Post by puppywhacker on 2009-02-24
No, your not overlooking something simple, you are overlooking something hard. I loaded your configs and got returned:

```
 host comet.xswitch.local
 Host comet.xswitch.local not found: 3(NXDOMAIN)

 dig @localhost comet.xswitch.local
 status: SERVFAIL, id: 61310
```

I added some debug into the named.conf from this random site
[http://www.netadmintools.com/art233.html]("http://www.netadmintools.com/art233.html")

The debug log showed me

```
 dns_rdata_fromtext: /etc/bind/db.xswitch.local:7: near eol: unexpected end of input
```

In line 7 the block ends where you defined the SOA, and that is where you lacked the email address like root@localhost (hardly recognizible though)

```
xswitch.local. IN SOA comet.xswitch.local. root.localhost. (
```

---

### Post by bluedalmatian on 2009-03-02
Thanks for that.  Id completely overlooked including the admin email address in it.

---

### Post by netztier on 2009-03-02
> **bluedalmatian said:**
> Im trying to setup a single BIND 9 DNS server on our (isolated) LAN for the domain xswitch.local
The primary DNS server will be comet.xswitch.local (192.168.254.200)

A recommendation:

Don't use **.local** as your local toplevel domain, as it will break avahi or make it disable itself:

[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

best regards

Marc

---

