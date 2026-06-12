---
title: "ldapsetpasswd doesn't change samba users password"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by sdmike6 on 2013-06-13
I'm using ubuntu 12.04 on two servers. One server is running OpenLDAP and the other is running samba.

Today I setup google PWM, which is awesome if you for HIPAA compliance, but I found an issue with samba.

If I'm on the OpenLDAP server and I run, $ sudo ldapsetpasswd <some user>. I'm not able to log into the samba share. BUT if I run $ sudo smbldap-passwd <some user> I'm then able to log into the samba share.

So I think google PWM is using ldapsetpasswd to change a users password.

Is there any way for me to make ldapsetpasswd to run smbldap-passwd?

---

### Post by sdmike6 on 2013-06-14
This might help: [http://www.openldap.org/lists/openldap-technical/200911/msg00004.html](http://www.openldap.org/lists/openldap-technical/200911/msg00004.html)

---

