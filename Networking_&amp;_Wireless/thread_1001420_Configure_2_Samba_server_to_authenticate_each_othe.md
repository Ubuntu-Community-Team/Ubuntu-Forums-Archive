---
title: "Configure 2 Samba server to authenticate each other"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by OfMacandMen on 2008-12-03
I was told this is the Holy Grail for System Admins

What we upgraded from:
- Single Windows 2003 SBS Server w/ AD that ran all service for 50U running Windows / Mac

What we currently are installing:
- Ubuntu 8.10 Server (Server) This server will act as the PDC (we have moved all users over)
- Ubuntu 8.10 Server (MediaServer). This is a file server (BDC) that will hold all users Home folders and Company Data folders

Here is what we are trying to accomplish.
- Allow the PDC & BDC to authenticate users on the network
- Provide a Single Sign-In Server for all users to easily access both server with out having to sign in each time.
- Run bat files to mount shares 

Our goal is to get far away from MS, so Likewise while a great product will no work because it still needs Windows AD.

---

### Post by Iowan on 2008-12-05
[This]("http://www.redhat.com/archives/k12osn/2008-August/msg00138.html") page has several links for LDAP - but I just noticed it's for RedHat. [Here]("https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html") is one that's a little closer to home.

---

