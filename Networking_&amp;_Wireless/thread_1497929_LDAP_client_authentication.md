---
title: "LDAP client authentication"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by laurent_waro on 2010-05-31
Hello everyone,
i try to log with GDM with users povided by LDAP. I followed instructions at [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) .
At this point I can :
-from a terminal with a "su", log with a ldap user.
-see the LDAP structure with "ldapsearch".
But I can't log with a LDAP user from gdm...

How can I do with gdm?

Here a piece of the message log file :
[I]gdm-simple-slave[870]: nss_ldap: could not connect to any LDAP server as cn=toto,dc=debian,dc=GRD,dc=FR - Can't contact LDAP server
gdm-simple-slave[870]: nss_ldap: failed to bind to LDAP server ldapi://192.168.10.2: Can't contact LDAP server[/I]

Someone can help me?

Note that i i install the package** libnss-ldapd** (instead of libnss-ldap), I can log with a LDAP user with gdm, but only if i logged with a _local user_ before!!!

Arrrgggghhhh!!!!!

---

### Post by box2 on 2010-06-14
Try adding this to your /etc/pam.d/common-session

session required        pam_mkhomedir.so skel=/etc/skel/

---

### Post by laurent_waro on 2010-06-14
Well,
after try severals ways, it's ok, I can log from GDM with LDAP. I have to go to job to see how i made it, and I will put the answer here tonight.

---

### Post by heruan on 2011-08-31
Which was the answer? Have you ever come home or something happened?! :-)

---

### Post by laurent_waro on 2011-09-01
lol!
I come to home...
But at work, I'll followed the solution of the [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication) with the correct packages.
And everything is ok.
I tried last month with a ubuntu server 10.04 and it worked too.

---

