---
title: "Trying to set up an LDAP server without DNS"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by oat328 on 2012-11-14
Hi all,

Trying to set up an LDAP server without DNS on 12.04.

Following this guide -- [https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)

When I get to step 3 under the "Post-Install Inspection," I type 
"ldapsearch -x -LLL -H ldap:///127.0.1.1." but i get the error 
"DNS SRV: Could not turn DN="127.0.1.1" into a domain"

I am not sure if my syntax is correct.  

Additionally, when it comes time to modify/populate the database, I am unsure what to substitute "dc=example,dc=com" with when I have no DNS service.

FYI, my /etc/hosts returns:
127.0.0.1       localhost
127.0.1.1       sw8

Anyone help would be very much appreciated.  Thanks.

---

### Post by oat328 on 2012-11-16
if there's any additional information you need, please let me know. 

thanks

---

### Post by luvshines on 2012-11-16
> **oat328 said:**
> When I get to step 3 under the "Post-Install Inspection," I type 
"ldapsearch -x -LLL -H ldap:///127.0.1.1." but i get the error 
"DNS SRV: Could not turn DN="127.0.1.1" into a domain"

I am not sure if my syntax is correct.

You'll need to fix 2 typos, remove an additional / and . from the URI

```
-H ldap://127.0.1.1
```

---

