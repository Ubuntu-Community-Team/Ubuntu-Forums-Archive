---
title: "HP Printer Sharing Woes"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by jmull86 on 2006-05-18
Im usinga desktop with Ubuntu as a personal server.  Ive got Samba and cups installed, and I can read the home folder from my XP laptop, but I cant get XP to see my printer.  I installed it through System / Admin / Printing.  The printer prints and scans fine from the desktop, but my laptop wont even see it, even though it sees my home directory fine.  Ive looked through the forums for similar problems, and I couldent find anything that seemed to fix my problems.  ANy help would be appreciated.  The Pringer is an HP PSC 1315.

---

### Post by mikexgough on 2006-05-19
I have Ubuntu 5.10 set up with samba and have cups installed, its a small network of 3x xp laptops and 1 workstation ( connected with HP PSC 1402), I had an Epson cx3600 connected to this and it worked fine and I just needed to put the windoze driver on the client(xp) machines. 
I set up samba as public as we are a family and the router is firewalled etc and secure. I set up samba using Webmin and the samba module, follow the insructions and it sets up ok, I have always been able to print ok from my clients but now I have installed the HP printer I can see all my pc's and the printer, from my xp clients but cant print from it, the forums here say use a net address to access and set up rather than a driver but hey i have set up per info here to no avail, i can see my printer but cant attach my clients to it.............

---

### Post by jmull86 on 2006-05-19
Well, I was looking around on HP's website, and it appears that the windows drivers arent made for network installs.  I cant seem to find just the driver for it.  Sharing works for me when the printer is hooked up to XP, and I think it would work if both computers were on Linux, but I dont think sharing will work with the printer on any windows clients.  Might be enough to persuade em to put ubuntu on my laptop though....

---

