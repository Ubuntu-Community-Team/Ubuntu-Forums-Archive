---
title: "Ubuntu network login?"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2008-12-18
Hi

I have an Ubuntu server and some WinXP clients that log into the samba domain and have their profiles etc. stored on the server. What i'd like to do is change all the clients to ubuntu but basically want it to work in the same way its working at the moment, ie 
users enter username and password which gets authenticated against their details on the server (so they can log into any machine on the network and have the same settings)

can this be done?

---

### Post by nixscripter on 2008-12-18
With entirely different software and hardware, the same effect can be acheived using an LDAP server. Take a look and see if it's what you want: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by Iowan on 2008-12-18
There is at least one other thread around here about logging into a Win2003 server and/or AD. One mentions [this]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/") page.  Someday I'm gonna get LDAP working here - just to learn how.

---

### Post by beaker15 on 2008-12-19
thanks guys, i think LDAP looks to be the way forward for me

---

