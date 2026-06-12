---
title: "SMB connection fails from one IP address only"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by maz_it on 2011-02-26
I have a 10.10 server running smbd for a shared directory. I can connect perfectly to it from any location except my home IP address. argh.

I am attempting connections to the samba server from 2 different computers running Mac OS X 10.6.6.

Here is what does work from the machines that can't connect to the samba share :
• SSH into the server 
• Ping server
• resolve host name
• ftps into server

There are no firewalls in place on either end. I can also connect to a SMB share I have running on a Mac server here in my office remotely so I know that my ISP is not blocking port 139 at all. 

There are no allow.hosts or deny.hosts entries.

I am at a total loss as to why just connections from my IP address on multiple computers would not work.

---

