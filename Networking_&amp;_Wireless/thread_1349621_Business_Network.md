---
title: "Business Network"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by dave.mcdaniel on 2009-12-08
Hello All,

I have a simple (well I think simple) question to ask about setting up a network in a small business environment.  First some background.

Business: IT service provider for small businesses ranging between 1-15 users.

Computer Environment: 5 Workstations. All using Ubuntu (from versions 8.04-9.04) 1 server (Ubuntu 8.04 server OS) running LAMP.

Scenario: I need to finish removing our Windows file server (it's running XP Home and it simply it old and unstable) and migrate to the Ubuntu server.  All of our data is on a 250GB slave hard drive that is currently sitting in the windows machine. I want to take that slave out and put it in the server and share it across the network.

Any ideas on how to best achieve this?  I need to have user permissions for the shared, and I think that Samba is not what I need because none of our machines use Windows.

---

### Post by AlexanderDGreat on 2009-12-13
You need to MOUNT NFS Home directories when the people login to the Ubuntu Server. You also need to authenticate them by NIS or LDAP. Finally, learn to use firewalls and proxy to filter Internet usage.

---

