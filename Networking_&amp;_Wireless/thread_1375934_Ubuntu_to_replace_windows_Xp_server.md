---
title: "Ubuntu to replace windows Xp server"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by dd1313 on 2010-01-08
Hi Guys..

We have 9 windows stations on XP and also Xp on the server to do file sharing.Now the boss wants a domain environment and
has asked me to look at Ubuntu

So what we want is filesharing, like word .xls ,pdf docs etc
Also we want to restrict what the user workstations can do.We want
to their profiles on the server, so when they login in
all profile information like the desktop, my documents
loads.If one PC for some reason gives in ,they can login on another and continue working.

I think this is called roaming profiles

So I am asking can I use Ubuntu  on the server for this

Thanks
Dev

---

### Post by Iowan on 2010-01-08
> **dd1313 said:**
> Now the boss wants a domain environment and
has asked me to look at [COLOR="Red"]FreeBsd[/COLOR].
 Typo? 
Ubuntu can act as a (Samba) file server, and (though I haven't yet done it) can use [LDAP ]("https://help.ubuntu.com/community/LDAPClientAuthentication"). [Another]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html") link for Samba and LDAP.

---

### Post by DGortze380 on 2010-01-08
While there are other authentication methods available.

(Like LDAP as previously mentioned)

The easiest thing to do (as far as overhead and reliability) is to just use Microsoft Active Directory.

If you want to peruse open source solutions:
[https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix](https://help.ubuntu.com/community/OpenLDAP-SambaPDC-OrgInfo-Posix)

---

### Post by dd1313 on 2010-01-08
> **DGortze380 said:**
> Microsoft Active Directory.


That would need MS small Business server atleast as I currently have XP on the server.Am I correct ?

thanks
Dev

---

### Post by DGortze380 on 2010-01-08
> **dd1313 said:**
> That would need MS small Business server atleast as I currently have XP on the server.Am I correct ?

thanks
Dev

Yes, you'd have to run some form of Windows Server and configure it as a Domain Controller.

---

