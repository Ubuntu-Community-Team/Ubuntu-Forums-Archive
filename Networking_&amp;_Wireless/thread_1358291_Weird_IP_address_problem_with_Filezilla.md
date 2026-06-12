---
title: "Weird IP address problem with Filezilla"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2009-12-18
Hi guys ...

I have a machine behind a router, with a static IP of 192.168.1.98. It's on a network with another machine, 192.168.1.20.

I have setup a vanilla copy of ProFTPd on the .98 server.

If I use the command line FTP program from the .20 machine, I can connect and tranfer files.

If I try to use Filezilla, I get logged in, then it just says (after a few seconds) "Error retrieving directory listing".

Messing around, I installed a copy of Filezilla on the .98 machine, and tried to FTP to 127.0.0.1 - same result.

I then tried the Network Config Wizard in Filezilla, and came across a weird issue ... no matter what I do, it insists that the machines IP address is my ISPs external IP address ... I have scoured all the network settings (using Webmin) but cannot find why it should think this. Telling Filezilla to use my internal IP address (192.168.1.98) doesn't seem to work.

Has anyone got any clue as to what is going on ?

---

### Post by Jethro_uk on 2009-12-18
problem was ProFTPd was configured to return my real IP address, rather than the servers. reconfigured & flying !!!!!!!!!

---

