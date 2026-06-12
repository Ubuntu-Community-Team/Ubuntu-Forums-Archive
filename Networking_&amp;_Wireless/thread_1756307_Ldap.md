---
title: "Ldap"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by iksanhariji on 2011-05-12
Dear All 

i have e problem when i konfigure ldap server in ubuntu 10.10 
if i type syntax 
root@pc05-KY848AA-AR6-CQ3032L:/home/pc-05# ldapadd -x -D cn=admin,dc=poligon,dc=org -W -f 
frontend.poligon.org.ldif 
Enter LDAP Password: 

massage

"ldap_bind: Invalid credentials (49)"

what is the problem.. can you help me

---

### Post by justanotherhack on 2011-05-12
Syntax looks okay and I assume you're using the correct password.

Could you try that with a higher debug level so we get more information? And maybe just use ldapbind to chase the problem, since it refers to it.

One thing that is a frequent problem with our users and LDAP authentication. Don't use characters in your password that are not ASCII. For example, language specific characters like German Umlauts cause trouble.

---

