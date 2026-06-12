---
title: "Sudden behavior change in Device URL of samba for XP printer"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by BoundaryValueProblems on 2009-11-28
Hi.  I encountered a very strange and sudden behavior change for my printer connected to Windows XP box.  My ubuntu version is 8.04 LTS; samba's version is 3.0.28a-1ubuntu4.9; and cups's version is 1.3.7-1ubuntu3.6.  I have been using these samba and cups to print things from my ubuntu boxes to this printer for a long time.
A couple of days ago, all of sudden, it stopped working.  My printer jobs were queued but never printed.  I checked the Printer Configuration, which says:
Device URL: smb://MSHOME/MYPC/Printer
as before.

Just in case, I changed this URL to the explicit IP address of my XP box at home as follows:
Device URL: smb://192.168.1.4/Printer

Then, it started working again.  I do not understand why the previous setting stopped working and I have to put the explicity IP address now.
Since this IP 192.168.1.4 may change depending on the router setting, etc., it is much more convenient to set the Device URL the previous way.

I do not think that I made any change on XP side, but I do not know whether some automatic windows update would cause such a behavior change or not.

Any suggestions/help would be greatly appreciated!
BVP

---

