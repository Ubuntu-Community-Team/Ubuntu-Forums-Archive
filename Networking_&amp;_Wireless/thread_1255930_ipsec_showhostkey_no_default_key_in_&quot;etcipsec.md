---
title: "ipsec showhostkey: no default key in &quot;/etc/ipsec.secrets&quot;"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by schapman43 on 2009-09-02
Alright, this is driving me nuts!  I would like to setup a VPN Site to Site tunnel with a couple Ubuntu servers.  However most of the documentation for doing so says to enter the following in a terminal 
ipsec showhostkey --left

However when I do this on both Ubuntu Servers a ubuntu desktop and laptop I get 
ipsec showhostkey: no default key in "/etc/ipsec.secrets"

I check ipsec.secrets and the only thing it has in it is the following
: RSA /etc/ipsec.d/private/HostnameKey.pem


What am I missing here? How do I get ipsec showhostkey --left to spit out the info that I want?

---

### Post by schapman43 on 2009-09-02
Any help would be greatly appreciated.

---

### Post by T3kG33k on 2009-11-05
Did you manage to find a solution to your plight?

---

