---
title: "How To Create OU in Ubuntu Server"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by janclients on 2012-01-26
Hi. I would like to know how to create OU in Ubuntu Server and once created how to make XP or Windows7 client login? Thank you.

---

### Post by SeijiSensei on 2012-01-26
Do you mean "OU" as in the LDAP field "organizational unit" or something else?

If you're looking for an LDAP server, you need to install **openldap**.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by janclients on 2012-01-26
> **SeijiSensei said:**
> Do you mean "OU" as in the LDAP field "organizational unit" or something else?

If you're looking for an LDAP server, you need to install **openldap**.

[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

yes, I meant  Organizational Unit like in Windows Based Server

---

### Post by SeijiSensei on 2012-01-26
I take it you're running an Active Directory server?

Are you looking to keep your AD server and connect Linux clients to it, or replace your AD server with a Linux alternative?  As I said above, if you're looking to replace an AD server with a Linux server and use it for single sign-on, then OpenLDAP is probably your best choice.  I'm not an expert on AD, though.  Maybe someone else can help.

---

### Post by janclients on 2012-01-26
No..I am going to setup a new server using a free server software (I am a newbie to LINUX) with 4 different OUs. Do you think LDAP will do the job or do you know any other that I should know just for learning. Thank you.

---

### Post by lisanels47 on 2012-03-26
[https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html)

Is the best setup guide.  

I also ran into some issues,but solved them.  See my thread: [http://ubuntuforums.org/showthread.php?t=1933111&highlight=ldap](http://ubuntuforums.org/showthread.php?t=1933111&highlight=ldap)

---

### Post by collisionystm on 2012-03-26
Use Zentyal. Its based on 10.04 LTS. Very easy to use. Has option for payed support and training if you want it.

---

