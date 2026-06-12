---
title: "“www” as CNAME"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by volmark on 2008-12-16
I can not find out how to add “www” to my zone as CNAME. I have tried a lot of syntax variations but in vain, the server does not respond as [www.mydomain.com](www.mydomain.com)
What’s wrong???

---

### Post by joebeasley on 2008-12-17
If you have access to your DNS, add an A record for www.  

If you must use a CNAME, just point www to a name that has an A record in DNS.

www  IN  CNAME   mydomain.com.

---

### Post by volmark on 2008-12-17
Unfortunately “www IN CNAME mydomain.com.” and A record don’t work. 
Note, I have checked the dot sign at the end, increased the serial and restarted bind9

---

### Post by volmark on 2008-12-18
Everything is stopped because I can not configure DNS properly :o(
What should I do now???

---

### Post by joebeasley on 2008-12-18
Post your named.conf and your zone files.

---

### Post by volmark on 2008-12-18
NAMED.CONF
.......................
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};


zone "85.in-addr.arpa" {
	type master;
	file "/etc/bind/db.85";
};

zone "venturetour.net" {
	type master;
	file "/etc/bind/db.venturetour.net";
};

include "/etc/bind/named.conf.local";

=========================================
db.venturetour.net
.......................
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns.venturetour.net. volmark.gmail.com. (
		     1512081358 	; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.venturetour.net.
@	IN	A	85.218.184.8
@	IN	AAAA	::1
ns	IN	A	85.218.184.8
www	IN	A	85.218.184.8
============================================

db.85
...........................
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns.venturetour.net. volmark.gmail.com. (
		     1512081346		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.venturetour.net.
@	IN	A	85.218.184.8
@	IN	AAAA	::1
ns	IN	A	85.218.184.8

===================================

:~$ sudo /etc/init.d/bind9 restart

 * Stopping domain name service... bind    

rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                               
[fail]

 * Starting domain name service... bind

---

### Post by volmark on 2008-12-19
Can anybody help me?? I’m bound to deadlines and some non-profits expect to place their sites on server before Christmas. I still hope that I can finish the setting up during a couple of days.  Please, help ...

---

