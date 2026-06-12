---
title: "DNS start fails - unknown option 'update-policy'"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by PeterOToole on 2011-03-06
Hi,

strarting my bind9 fails with this error in /var/log/syslog:

```
Mar  6 11:27:50 myserver named[28790]: loading configuration from '/etc/bind/named.conf'
Mar  6 11:27:50 myserver named[28790]: /usr/local/samba/private/named.conf.update:2: unknown option 'update-policy'
Mar  6 11:27:50 myserver named[28790]: loading configuration: failure
Mar  6 11:27:50 myserver named[28790]: exiting (due to fatal error)
```I am trying to use samba 4 and made all steps as mentioned.

Does anyone knows where to put the option 'update-policy'.

Regards,

PeterOToole

---

### Post by lncoll on 2011-03-06
I don't know about Samba, but the best is you post your /etc/bind/named.conf to see what is the mistake.
Elsewhere in /etc/bind/named.conf is better do not write directives, only include other conf files.
The most used named.conf file is:
```

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

```

---

