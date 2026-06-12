---
title: "Connecting to a domain"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by dptulk on 2009-01-12
Howdy all, I am trying to get myself up and running inside of a Win2000/2003 domain.  I am running Ubuntu 8.10 and so far all seems good.  I need to start accessing some of the files on the network shares and i'm at a loss.  Where do I start?  Is there a "client" that I need to install to get my "user" authenticated for the domain? 

Thanks
Dave

---

### Post by albinootje on 2009-01-12
> **dptulk said:**
> Howdy all, I am trying to get myself up and running inside of a Win2000/2003 domain.  I am running Ubuntu 8.10 and so far all seems good.  I need to start accessing some of the files on the network shares and i'm at a loss. 

Did you try -> Places -> Connect to Server already ?

Take also a look at this :
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#ads-member](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#ads-member)

And I don't know whether the W2000/2003 Domains can do any Active Directory, if so, see here :
[https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

[http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html](http://www.bauer-power.net/2008/05/join-ubuntu-804-to-windows-domain.html)

Check also the client part of this :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

