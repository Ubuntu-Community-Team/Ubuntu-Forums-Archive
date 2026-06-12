---
title: "Want to start learning about nerworking"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by thebrotherofasis on 2009-05-21
Hello,

I have small business where we use 6 computers, all running Ubuntu 9.04. All the machines are connected to the internet, some via wireless and some through a trendnet router.

Here's what I want to do (please, beware that I have no experience in networking, besides simple Samba File sharing):

I would like to be able to make one of the 6 computers behave like a Server, and the other machines connect to that server, and work from it. The Clients (the other 5 computers) would operate their own sessions through the server, opening programs, browsing, saving files, etc, FROM the server's resources, and not from their own.

If I turn on one of the client machines, I want to be able to tell Ubuntu to connect to the server, and open a session from there.

How is this called?

I want to try this, because I would like to look for the possibility of acquiring some inexpensive machines, that can work as clients of a server, saving hardware costs.

I would just appreciate if you can give me some general information on how to do that, and how this is called, so that I can look up the info in Google.

Thank you.

---

### Post by Iowan on 2009-05-21
Kinda sounds a little like [LDAP]("https://help.ubuntu.com/community/OpenLDAPServer").

---

### Post by ktrnka on 2009-05-22
Sounds kinda more like LTSP.

[https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")

---

### Post by thebrotherofasis on 2009-05-22
Thank you!

I'll look into that.

L

---

### Post by Iowan on 2009-05-22
> **ktrnka said:**
> Sounds kinda more like LTSP.That was my first thought - but didn't know how "thin" 9.04 is...

---

