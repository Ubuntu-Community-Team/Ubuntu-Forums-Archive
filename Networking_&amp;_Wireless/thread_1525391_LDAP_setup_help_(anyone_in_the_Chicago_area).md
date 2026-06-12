---
title: "LDAP setup help (anyone in the Chicago area???)"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by gforster on 2010-07-06
I am trying to setup LDAP and NFS for our school computer lab (authenticating student logins, file storage, etc.) but I am in over my head. I can't seem to find a good guide for 10.04 anywhere. It would be great if there were someone local that could come help me out in person. Or a good guide that is clear and accurate if anyone knows of anything.

---

### Post by bkratz on 2010-07-06
> **gforster said:**
> I am trying to setup LDAP and NFS for our school computer lab (authenticating student logins, file storage, etc.) but I am in over my head. I can't seem to find a good guide for 10.04 anywhere. It would be great if there were someone local that could come help me out in person. Or a good guide that is clear and accurate if anyone knows of anything.



I know nothing about those but maybe these can help?

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by gforster on 2010-07-07
> **bkratz said:**
> I know nothing about those but maybe these can help?

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

The problem is that those guides are outdated. I need something to work with 10.04

---

### Post by bkratz on 2010-07-07
> **gforster said:**
> The problem is that those guides are outdated. I need something to work with 10.04




Will look some more, this stuff is date April 2010, maybe something there?

[http://www.openldap.org/doc/admin24/](http://www.openldap.org/doc/admin24/)

---

### Post by azan00 on 2010-07-07
Hello, I too am attempting to setup the same thing you are. I couldn't follow most of the guides out there because like you said, they aren't written for 10.04.


I found this guide for setting up a server in 10.04. It also contains links to setting up phpldapadmin and a client as well.

[http://tuxnetworks.blogspot.com/2010/06/howto-ldap-server-on-1004-lucid-lynx.html](http://tuxnetworks.blogspot.com/2010/06/howto-ldap-server-on-1004-lucid-lynx.html)


Good luck! I am currently stuck on setting it up to work with NFS, but authentication works.

---

### Post by gforster on 2010-07-08
> **azan00 said:**
> Hello, I too am attempting to setup the same thing you are. I couldn't follow most of the guides out there because like you said, they aren't written for 10.04.


I found this guide for setting up a server in 10.04. It also contains links to setting up phpldapadmin and a client as well.

[http://tuxnetworks.blogspot.com/2010/06/howto-ldap-server-on-1004-lucid-lynx.html](http://tuxnetworks.blogspot.com/2010/06/howto-ldap-server-on-1004-lucid-lynx.html)


Good luck! I am currently stuck on setting it up to work with NFS, but authentication works.

Thanks for the link. That should be helpful. What problems are you experiencing with NFS? I am interested as I plan on using NFS with this setup.

---

### Post by azan00 on 2010-07-09
I think it's an NFS problem, to be honest I am quite ignorant about all this. But when I attempt to login I get an Unable to Update ICEauthority file error.

I assume this is because ldap or nfs is not creating the proper home directory files. It appears that it mounts the home directory correctly, but there are no default files setup for them.

---

