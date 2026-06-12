---
title: "Ldap replication"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by Ravi Chandra on 2009-05-27
Hi all,

Pl. excuse if its wrong place to post. But redirect to me to best place.

I have Ldap up and working setup around 4 yrs ago in my organization by some other person. This is used by ftp,mail,webserver,proxy..etc. 

Load being high I am noticing significant delay in authenticating, Hence I want to replicate onto ubuntu server edition.

Pl. lettme know how to do this?? 
Now that I have installed openldap. How to Export and Import data & settings from one to other?
Any other good option?

Thanks,
r.

---

### Post by puppywhacker on 2009-05-27
I only used slurpd which is now replaced by syncrepl, I haven't set it up yet. The openldap documentation has always been very solid.

[http://www.openldap.org/doc/admin24/replication.html]("http://www.openldap.org/doc/admin24/replication.html")

---

