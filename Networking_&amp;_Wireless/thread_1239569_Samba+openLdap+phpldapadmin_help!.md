---
title: "Samba+openLdap+phpldapadmin help!"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by rentacop on 2009-08-13
Hey everyone, I have been searching around the web for a few days now with no luck at all.

Heres my setup.

ubuntu  server

Samba as a domain controller -installed and working.
openLdap - installed and running.
phpldapadmin - installed and working.


--

I am having an issue with connecting an XP machine to a domain though phpldapadmin. 

when i manually add a machine in samba it works fine. example below.

useradd netbios$
smbpasswd -a -m netbios$
smbpasswd -a user


However when i create a user using phpldapadmin it allows me to enter the username and password but it says the user must change his password on the first login, after i change the password it says 'you do not have the rights to change your password'

i also disabled the requirepasschange on login though phpldapadmin and its still asking me to change the password on login.

any help would be appreciated.

---

