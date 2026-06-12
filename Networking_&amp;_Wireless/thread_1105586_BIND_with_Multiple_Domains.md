---
title: "BIND with Multiple Domains"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by jpfulton on 2009-03-24
Let me first start by saying that I've read many of the available resources for figuring this out and I'm still having trouble. I read another post of the ubuntu forums with almost the same thread title but still can't get it right.

I want to setup one BIND DNS Server to manage records for two different public domain names. I'm running 8.04.

I've checked this out with pingability.com and while the first zone works perfectly, the second zone has multiple errors. The errors include "No host (A) record. No MX record." (and more) Everything I read makes it looks like this is write. Please let me know if I need to provide more info. THANKS!

named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "royaloakproofsite.com" {
	type master;
	file "/etc/bind/royaloakproofsite.com.hosts";
        allow-query { any; };
        allow-transfer { 66.184.65.74; };
};
zone "bosshotline.com" {
	type master;
	file "/etc/bind/bosshotline.com.hosts";
	allow-query { any; };
        allow-transfer { 66.184.65.74; };
};

```

royaloakproofsite.com.hosts (Zone 1):
```
$ttl 38400
royaloakproofsite.com.	IN	SOA	ns1.royaloakproofsite.com. jpfulton.royaloakproofsite.com. (
			1055026220
			6H
			1H
			5D
			20M )
royaloakproofsite.com.	IN	A	66.184.65.74
mysql	IN    A     66.184.65.74
www	IN    CNAME royaloakproofsite.com.
royaloakproofsite.com.        IN    NS    ns1.royaloakproofsite.com.
royaloakproofsite.com.        IN    NS    ns2.royaloakproofsite.com.
royaloakproofsite.com.	IN	MX	5 mail.royaloakproofsite.com.
mail	IN	A	66.184.65.74

```

bosshotline.com.hosts (Zone 2):
```
$ttl 38400
bosshotline.com.	IN	SOA	ns1.royaloakproofsite.com. jpfulton.bosshotline.com. (
			1055026224
			6H
			1H
			5D
			20M )
bosshotline.com.	IN	A	66.184.65.74
bosshotline.com.	IN	NS	ns1.royaloakproofsite.com.
bosshotline.com.        IN      NS      ns2.royaloakproofsite.com.
bosshotline.com.	IN	MX	10 mail.bosshotline.com.
mail			IN	A	66.184.65.74
mysql			IN	A	66.184.65.74
www			IN	CNAME	bosshotline.com.

```

---

