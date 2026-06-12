---
title: "Can't connect to my Windows shares and printer"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by gml_josea on 2009-11-11
I've got two desktops and a laptop connected with my router. The desktops are running Windows 7 and the laptop dual-boots Windows 7 and Ubuntu 9.10. The desktops accounts are password protected. The problem is that when I'm on Windows I can access my network shares and printer without any issues, but when I'm on Ubuntu I can't get it to see the network (and the Windows desktops also fail to detect my laptop in Ubuntu). However, when I had XP on these desktops Ubuntu didn't have any problems connecting to them and accessing the printer, but when I upgraded to Windows 7 everything stopped working.

EDIT: I followed a guide and managed to make Samba show my desktops, however, when I try to access them samba asks me for the username and password. I put the appropiate usarname/password for the desktop I'm trying to access but it doesn't let me in, it shows me the username window again.

Is there a fix or workaround for this?

Thanks you.

---

### Post by r+9 on 2009-11-12
may be a dumb question, but did you check to see if the printer was linux friendly?  I gave away my lexmarx because it wouldn't play nice.

---

### Post by gml_josea on 2009-11-12
Yes it does, it used to work when that desktop was running Windows XP, but after I installed Windows 7, ubuntu couldn't see it anymore.

---

### Post by Nick_NS on 2009-11-22
I am having a similar issue with my EeePC running karmic. I recently updated my desktop pc to Windows 7 Home Premium. Two other Windows XP machines are able to access shares on the Windows 7 desktop.

In Karmic however, when I try to access those same shares, I get a prompt for a username/domain/password. After entering the required info and continuing the prompt reappears. It does not give an incorrect info error or anything like that, it simply loops back to the prompt. Same thing for accessing the shared printer attached to the desktop.

The same issue is repeatable using VirtualBox running Karmic.

Anyone had any luck around this?

---

### Post by Nick_NS on 2009-12-03
I have found a workaround for this issue with regards to shared folders at least. If you install smbmount, you can then mount the Windows 7 share to a local folder. This may be cumbersome but it will at least give you the connectivity you need until they fix whatever is causing the issue.

---

