---
title: "Local logon"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by netz_partol on 2010-09-13
Hi,
I'm a new administrator of an ubuntu network. There are a bunch of PC's clients and an ubuntu server with the Webadmin for user/groups control. Users log on to the clients with roaming profiles.

How do I log on to the clients locally to install software?
Maybe this goes in the absolute beginner forum, but I think it's a bit more advanced:KS,

---

### Post by MaindotC on 2010-09-13
Just hired and got thrown to the wolves eh?

When you say a ubuntu network - is there a central OpenLDAP or Active Directory server that all the clients authenticate?  If not, do you have an administrative account for all of the machines?  If so just can ssh to each machine and install whichever software you need using the shell.

---

