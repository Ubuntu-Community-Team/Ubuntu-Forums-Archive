---
title: "Domain name for Hostname"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by banghere2 on 2012-11-23
I have following entry in /etc/hosts
127.0.0.1	localhost
127.0.1.1	myusername

I needed to find out my domain name so that i could correct the above format of the entry and enable smtp to send mails. I needed something like this (as per googling):
 127.0.0.1     localhost localhost.localdomain myusername
But I cannot determine my domain name. I tried following commands but nothing gave me the answer.

$hostname -d
returned empty string

$nslookup 127.0.0.1
Server:		127.0.0.1
Address:	127.0.0.1#53
1.0.0.127.in-addr.arpa	name = localhost.


$domainname
(none)

$nslookup 127.0.1.1
Server:		127.0.0.1
Address:	127.0.0.1#53
** server can't find 1.1.0.127.in-addr.arpa.: NXDOMAIN

Please Help. I am a newbie so sorry if there is some mistake.

---

### Post by bab1 on 2012-11-23
> **banghere2 said:**
> I have following entry in /etc/hosts
127.0.0.1	localhost
127.0.1.1	myusername

I needed to find out my domain name so that i could correct the above format of the entry and enable smtp to send mails.
The domain name is something you create (and register if it is for the public internet).  Have you defined a a DNS domain name (i.e. domain.com)?> 

I needed something like this (as per googling):
 127.0.0.1     localhost localhost.localdomain myusername
[/CODE]This is wrong for 2 reasons.  You do not put your name in the /etc/hosts file.  You will need to map the hostname and domain to the IP address of the network adapter interface.```


But I cannot determine my domain name. I tried following commands but nothing gave me the answer.

$hostname -d
returned empty string
If you want the hostname only you use [CODE]hostname
```...if you have not defined a domain then *hostname -d *will not show the domain.  What do you get with just using *hostname*> 
$nslookup 127.0.0.1
Server:		127.0.0.1
Address:	127.0.0.1#53
1.0.0.127.in-addr.arpa	name = localhost.


$domainname
(none)

$nslookup 127.0.1.1
Server:		127.0.0.1
Address:	127.0.0.1#53
** server can't find 1.1.0.127.in-addr.arpa.: NXDOMAIN

Please Help. I am a newbie so sorry if there is some mistake.
The IP address 127.0.0.1 is only used for the local machine (localhost).  It is not used to communicate from one host to another.

You need to define the the *hostname.domain_name.tld* in at least the /etc/hosts file for each machine (or use DNS), so you need to determine the hostname and create a domain name (local or public).

---

### Post by Sergius14 on 2012-11-23
By default it is just ```
.local
```

```
hostname -A
```


Check this out:

[http://www.subvs.co.uk/ubuntu_change_hostname_computer_name](http://www.subvs.co.uk/ubuntu_change_hostname_computer_name)

Also: Do not use Public Internet domain names for internal purposes.... event .net. This could lead to public/external DNS queries or network errors.

Keep it .local.

Except, of course, that your are going to put a public SMTP server

like:


mylocalmachinename.mylocaldomainname.local

---

### Post by banghere2 on 2012-11-24
I created Domain (local) from cli and smtp (for a tracking system) is working just fine.
Thank you guys....

---

