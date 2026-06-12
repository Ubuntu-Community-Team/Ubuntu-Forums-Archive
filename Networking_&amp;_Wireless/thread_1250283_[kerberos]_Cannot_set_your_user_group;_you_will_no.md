---
title: "[kerberos] Cannot set your user group; you will not be able to log in."
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by martijntje on 2009-08-26
I am trying to log in using kerberos credentials. This works fine if there is a local user with a username matching the kerberos principal name, however, in every other case I get the following error:
 
> Cannot set your user group; you will not be able to log in. Please contact your system administrator.

I already have the /home folder mounted with nfs and authentication works through kerberos. I can of course set up openldap, but is this possible without it?

---

