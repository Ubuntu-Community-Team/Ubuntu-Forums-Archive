---
title: "Modify bash prompt based on SSH login hostname/CNAME"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by dreville on 2012-12-18
Hi,

I have a proper naming scheme for the servers and devices on our network. However, I plan to use CNAMEs to make it easier for end-users to login into certain servers. 

e.g. 
PHT-DB-01.  A  192.168.2.30.
happy.  CNAME  PHT-DB-01.

Is there a way to use the CNAME (happy) in the bash prompt if the end-user connects via ssh to the same server (PHT-DB-01) using user@happy?

i.e. 
login: ssh user@PHT-DB-01
prompt: user@PHT-DB-01:~$

or

login: ssh user@happy
prompt: user@happy:~$

Thank you for your advice!

---

