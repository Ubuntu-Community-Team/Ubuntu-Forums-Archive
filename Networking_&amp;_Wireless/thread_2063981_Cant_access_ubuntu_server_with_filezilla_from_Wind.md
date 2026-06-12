---
title: "Cant access ubuntu server with filezilla from Windows."
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by marjoh05 on 2012-09-28
Greatings.

I'm working on a new lamp/samba server, because we need some better hardware.

I moved over the www directory, and moved over the databases (used phpadmin)

But still the pages wont open.

i made a info.php in the WWW directory, it worked.

i have checked permissions in /var/www everything is identical to the old server.

I cant access the ubuntu with filezilla for some reason, i think it may be a connection with the web not working?
There is no problem to login on the old server.

Any ideas?

My English is not perfect, but you'll get the point :-)

Regards
Marjoh05
Ict-apprentice

---

### Post by marjoh05 on 2013-01-02
Bump.

---

### Post by CraigThomas on 2013-01-05
> **marjoh05 said:**
> 
i have checked permissions in /var/www everything is identical to the old server.


What are those permissions?


> **marjoh05 said:**
> 
I cant access the ubuntu with filezilla for some reason, i think it may be a connection with the web not working?
There is no problem to login on the old server.


I believe it's common to add the user to a group which may have then had permissions to the /var/www folder on the old system.

I'm no expert but these two points may give you something to look at.


Craig

---

