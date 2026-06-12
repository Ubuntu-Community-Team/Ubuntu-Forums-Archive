---
title: "Simple Ubuntu SOHO/LAN setup?"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by farproc on 2011-05-19
I have a small network comprising all of about 3 workstations that Ive migrated off of XP Home, onto Ubuntu.

With XP Home I was just using a simple Workgroup, with user accounts configured on each PC. With XP it was convenient (necessary) to simply have each user an Admin otherwise permissions on the workgroup became a pain.

With the move to Ubuntu I was contemplating trying to fix this situation by ... I don't know - setting up an Ubuntu server to centralize the various spreadsheets and quotes to be accessible from any workstation and perhaps even try to centralize user account management rather than creating the accounts over and over on each workstation.

Given that everything is Ubuntu and there is no windows on this network at all, is Samba necessary? What simple things can I do to get a basic "workgroup" with a printer and some shared folders going?

---

### Post by drdos2006 on 2011-05-19
You could use one of the desktops to act like a server.
Install network file sharing server on that machine.
Select a folder to share, alter /etc/exports to tell Ubuntu to share the folder.

On each workstation install the network file sharing client.
Mount the shared folder over the network and there you have it.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)

regards

---

