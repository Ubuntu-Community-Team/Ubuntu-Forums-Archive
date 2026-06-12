---
title: "Samba: cli_start_connection: failed to connect to ... problems"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-03-20
Hi all,

Have a slight samba problem here after solving some others.  This one has me scratching my heads.

Three machines on the network with identical (of so i think) samba configs.

machines are 

 ubuntu 8.10
xubuntu 8.10
 ubuntu 8.04 Server

the ubutnu's are fine.  However the xubuntu is giving the error shown in the attached png picture file.

---

### Post by sefs on 2009-03-20
some how it seems resolv.conf was the culprit here...

it had some "searh www.namehere.com" field at the top that was throwing off resloving for samba plus the dns entry below it.  I deleted the searh line and things looks to be back to normal so far.

---

### Post by sefs on 2009-03-21
One last problem remains...

pyNeighborhood is failing to scan workgroup WORKGROUP

It can however still add a machine and mount the share directly from the "Edit" menu.  That's if you know the name of the machine.

But why is it failing to scan the workgroup and show the machines within it.

---

### Post by sefs on 2009-03-21
I upgraded from ver 0.4 available in repos to ver 0.5 available from launchpad ([https://launchpad.net/~encbladexp/+archive/ppa](https://launchpad.net/~encbladexp/+archive/ppa)) things work much better.

---

