---
title: "Network configuration Ubuntu Windows RouterOS"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by pouvouv on 2010-08-04
Hi,
We are quite new in setting up a network using Ubuntu, and currently we are setting up a network using Ubuntu Desktop for file server.

What we wanted is that a user log in using their desktop (can be Ubuntu or windows as we are currenty rolling out the use of windows system) and put in their user name and password and they get all their folders, access (internet and intranet) and what on their desktop shown (they can use different computer but the result is similar, like what i notice in a university). We also wish that the user could change their given password on their own system, which then update the password on the rest of the system.

We currently use mikrotik router and they recall that the internet settings can be linked via a RADIUS server. We looked at other people opinion on internet and suggest to use SAMBA server then use it to configure RADIUS server for authentication. 

Would that be the normal way to do it on Ubuntu for multi platform client? Are there any easier way to do that?

Thank you very much for your time.

Cheers,
erick.


Current system configurations:
Router software:
- RouterOS (Mikrotik)
Server OS:
- Ubuntu Desktop
Client OS:
- Ubuntu Desktop
- Windows

---

### Post by Iowan on 2010-08-04
Sounds a bit like LDAP, but I haven't really investigated...

---

