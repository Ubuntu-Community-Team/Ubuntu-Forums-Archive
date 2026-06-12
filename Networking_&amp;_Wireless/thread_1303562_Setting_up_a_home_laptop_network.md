---
title: "Setting up a home laptop network"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by melacoby on 2009-10-28
Hi, have been using (and loving) ubuntu for the pass couple of months, and have been able to really use my computers to their true potential. Now I am interested in setting a wireless network at home and need some help on where and how to start this quest. As for now I use a linksys wireless router to connect to the Internet (3 laptops). I intent to (if possible) have the older laprop Dell inspirion e1405 as the main computer (kind of like the server?) connected to a external hard drive, the printer  and the tv if I am able to make it into a dvr. This one will stay on most of the time. Then access its information, including the external hard drive and prinitng from anywhere in the house using the other computers. The question I guess will be; Do I need anything else other than the router and what I have? Is it too much to handle for just one machine? Am I ignoring stuff I need to know?
Any help will be greatlly apperciated!

---

### Post by Ghostbear121 on 2009-10-28
Sure, it's a little more uncommon to use a notebook as a server, but it's more than powerful enough to handle some file sharing and stuff.

Just set it up, give eth0 its own static IP address, and start installing some services like Samba (for files and printers).  Include some firewall rules using IPTables.  Basically this is your basic Samba server setup, and you can follow any HowTo for specific info, or just ask here.

---

