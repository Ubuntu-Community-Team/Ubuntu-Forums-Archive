---
title: "dhcp adds extra dot to the end of domain name"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by supremedalek on 2009-11-13
I have something interesting happening and I do not know if it is on my desktop (ubuntu 9.04) or on our dhcp server. Let's say my desktop is called, well, desktop and I have set it up to get its IP using dhcp (through NetworkManager). When it obtains the IP, the /etc/hosts file is edited with the following line added:

```
127.0.1.1       desktop.internal.domain.com.    desktop
```

Note the dot on the end of the domain. Why is it there? How did it get there? At first I was ready to blame NetworkManager, but I have a debian 5 and an ubuntu 9.04 servers (installed the latter using the ubuntu server cd) and they show the very same behavior. 

I checked our dhcp server and its dhcpd.conf file begins like this:

```
ddns-update-style interim;
ignore client-updates;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.11.255;
option routers 192.168.11.1;
option domain-name "internal.domain.com.";
option domain-name-servers 192.168.11.1;
option ntp-servers us.pool.ntp.org;
option ldap-server code 95 = text;
option ldap-server
"ldap://ldapserver.internal.domain.com/dc=domain,dc=com";
option domain-search-order code 119 = string;
option domain-search-order "internal.domain.com. domain.com.";
[...]
```

Why would the domain names end with a period in this file? If I am not
mistaken, that is done in the bind stuff, but not here. Am I correct or
confused as usual?

---

### Post by puppywhacker on 2009-11-13
You are right about the bind dns server configuration where a dot means the absolute/fully qualified domain.

Your dhcpd.conf contains two times a weird . at the end where I don't think there should be any.

```
option domain-name "internal.domain.com[COLOR="Red"]**.**[/COLOR]";
option domain-search-order "internal.domain.com[COLOR="Red"]**.**[/COLOR] domain.com[COLOR="Red"]**.**[/COLOR]";

```

I find it weird that netmanager adds entries to the host file and not let the dns server take care of it.

---

### Post by sawick61 on 2009-11-13
> **puppywhacker said:**
> You are right about the bind dns server configuration where a dot means the absolute/fully qualified domain.

Your dhcpd.conf contains two times a weird . at the end where I don't think there should be any.

```
option domain-name "internal.domain.com[COLOR=Red]**.**[/COLOR]";
option domain-search-order "internal.domain.com[COLOR=Red]**.**[/COLOR] domain.com[COLOR=Red]**.**[/COLOR]";

```I find it weird that netmanager adds entries to the host file and not let the dns server take care of it.

"dots" are null characters anyways it won't affect anything

---

### Post by supremedalek on 2009-11-13
In my case they are. Let's say I install ssmtp to send emails. Ubuntu will create the ssmtp.conf file with the hostname (for the return address) with the dot on the end, and that is being considered spam by our spamassassin (FH_HELO_ENDS_DOT 2.31).

---

