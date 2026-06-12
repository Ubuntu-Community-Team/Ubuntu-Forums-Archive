---
title: "home network printer server"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by Jockboy98295 on 2013-01-08
Trying to set up my desktop (Ubuntu 10.01) as a home print server. Problem is my wifes laptop (winndows 7) will not "see" my desktop on my network. Everything else is working perfectly. If anything all I need is for her computer to be able to print from the printer, which of course is hooked up to the desktop. Any help is greatly appreciated. Thanks.

---

### Post by kurt18947 on 2013-01-08
What printer?  If this is a stupid question, apologies in advance but does the printer have built-in networking?  I prefer to have printers connected via my router - wired or wireless - rather than to a PC.  I find that simple, reliable and OS agnostic.  If a printer is attached to a PC, that PC must be powered up in order to print.  Attached to a router, only the router must be powered up in order to print.  If the PC is left on all the time anyway, ignore me :razz:.  I suspect you'd need Samba to print from a Windows machine to a printer attached to Ubuntu machine but I have no idea what's involved.

---

### Post by Jockboy98295 on 2013-01-08
lol. Not a stupid question. The printer is hooked up to my desktop, the desktop is never shut down. The desktop is the "hardware firewall" and router. lol. The cable modem is hooked up to the desktop, and the desktop throws the wireless. That way I dont worry about viruses and such on the windows computers. So far, everything works perfect, except I cant get her stupid computer to see the printer. :( And the printer has no network capability on its own, so no luck for me. :(

---

### Post by kurt18947 on 2013-01-09
I'm clueless about this stuff.  You might do a google search using samba+print server.  Here is one 'official' page:

[https://help.ubuntu.com/10.04/serverguide/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/samba-printserver.html)

This looks really simple.  I'm sure that's really deceptive :D  Maybe somebody who's been through this - with the bruises to prove it ;) - will check in.

I did have an HP Deskjet working for a while using a Netgear ps-101 print server that I'd had for years.  It was surprisingly simple and worked surprisingly well but when the ink needed replacing, two replacement ink cartridges cost nearly as much as the Brother MFD with wired and wireless networking that replaced it.  New print servers have the same problem - stand alone print servers cost as much as print servers with printer/scanner/faxes attached to them.

---

### Post by Jockboy98295 on 2013-01-13
Thanks folks. Ive gone through 4 different samba set-up tutorials (one from samba themselves) to no avail. lol. total pita. oh well. ill figure something out. Thanks.

---

