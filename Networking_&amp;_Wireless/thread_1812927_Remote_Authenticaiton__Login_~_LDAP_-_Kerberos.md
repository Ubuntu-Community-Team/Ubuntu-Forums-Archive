---
title: "Remote Authenticaiton / Login ~ LDAP - Kerberos"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by Ziyan Junaideen on 2011-07-27
I am interested learning about networks in Linux and prefer to use Ubuntu. I hope the title is reflects what I really need to know. If not sorry about that.

I have an requirement, it is to have a server to handle authenticaition of users so generally users can use that server to use specific services such as login (to linux), mail (postfix) and perhaps a file server (to hold user data, lets say what we have on /home/[username])

I did some reading, and it looks like I will need LDAP and Kerberos. But I couldn't get a good understanding on how to practically deploy such a service.

I would be obliged if some you guys can give me some guidelines on how to achieve my goal. Topics I need to read, books I could refer would be a plus. :popcorn:

To tell you some thing about me, I am not a *NIX guy, my knowledge is kinda just above basic. :D

I am using an updated Ubuntu Server 10.04 LTS, is it a bad idea? Should I go for Ubuntu latest. Ubuntu 11.04 kind of got stuck after an update.

Thank you in advance.

---

### Post by newbie-user on 2011-07-27
Here's a small list of things to get you started in the right direction:

OpenLDAP - Directory services, package to install is slapd
Samba - File server for Windows clients, package is samba
NFS - File server for Linux clients, package is nfs-kernel-server
Postfix - package is postfix, great tutorials here: 
[http://www.postfix.org/docs.html]("http://www.postfix.org/docs.html")
OpenSSH - Remote management, package is openssh-server

Ubuntu 10.04 LTS is preferable for production servers, but for testing and/or learning, it really doesn't matter.

---

