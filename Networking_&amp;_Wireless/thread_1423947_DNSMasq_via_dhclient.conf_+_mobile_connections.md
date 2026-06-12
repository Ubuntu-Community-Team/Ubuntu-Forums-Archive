---
title: "DNSMasq via dhclient.conf + mobile connections"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2010-03-07
I'm using DNSMasq to speed up DNS lookups. In dhclient.conf I have a line that says

```
prepend domain-name-servers 127.0.0.1;
```

Works brilliantly..in resolv.conf I get 127.0.0.1 at the top after connecting to a wireless nework.

BUT - not when I connect with my HUAWEI USB-stick to the mobile network! The speedup DNSMasq offers could really be of use but I just noticed 127.0.0.1 in this case is NOT added to resolv.conf.

Why not? Has anyone else run into this?

**later**

Ok, seems dhclient.conf isn't used when doing PPP (modem)-stuff. I get the feeling I should be able to create some sort of script in /etc/ppp/ip-up.d that does DNS2="$DNS1" and DNS1="127.0.0.1". I'm mucking about with this but don't really know what I'm doing.. Could someone please lend me a hand?

---

