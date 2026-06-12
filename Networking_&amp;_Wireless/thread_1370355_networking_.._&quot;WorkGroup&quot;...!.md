---
title: "networking .. &quot;WorkGroup&quot;...!"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by 0863588 on 2010-01-02
hi ):P ... good Evening to every 1 .

I am new to using "Linux ubunto".
 
I want to be defined on the network "workgroup"....?? THANKS

---

### Post by peepingtom on 2010-01-02
Hi, 


Press alt+f2. Run this command:```
gksudo gedit /etc/samba/smb.conf
``` Edit your Workgroup name and save the file. Restart samba or your computer.

---

### Post by 0863588 on 2010-01-02
> **peepingtom said:**
> Hi, 
 
 
Press alt+f2. Run this command:```
gksudo gedit /etc/samba/smb.conf
``` Edit your Workgroup name and save the file. Restart samba or your computer.
 
[SIZE=4][COLOR=black]**_Thanks ..... I will do it . _**[/COLOR][/SIZE]
[SIZE=4]But can i know the meaning of _"**SAMBA**_"..??:confused:[/SIZE]
[SIZE=4]And  Also how do i restart **_"SAMBA_"..?:confused:**[/SIZE]

---

### Post by peepingtom on 2010-01-02
Samba shares files to and from windows computers.
[http://en.wikipedia.org/wiki/Samba_%28software%29](http://en.wikipedia.org/wiki/Samba_%28software%29)
Restart your whole computer after editing the file, that is the easiest way to restart Samba.

---

### Post by PAKSHAN on 2010-01-05
In computer networking, a **workgroup** is a collection of computers on a [local area network (LAN)]("http://compnetworking.about.com/library/glossary/bldef-lan.htm") that share common resources and responsibilities. Workgroups provide easy sharing of files, printers and other network resources. Being a [peer-to-peer (P2P)]("http://compnetworking.about.com/library/glossary/bldef-p2p.htm") network design, each workgroup computer may both share and access resources if configured to do so.  The Microsoft Windows family of operating systems supports assigning of computers to named workgroups. Macintosh networks offer a similiar capability through the use of **AppleTalk zones**. The Open Source software package [Samba]("http://compnetworking.about.com/library/weekly/aa062499.htm") allows Unix and Linux systems to join existing Windows workgroups. 

===============================================
[LIMS Software](http://labface.com/suppliers/LIMS-Software-33)
[affiliate guide](http://www.affiliateleap.com/)

---

### Post by Morbius1 on 2010-01-05
To restart the samba service:

Open **Terminal**
Type **sudo service samba restart**

---

### Post by 0863588 on 2010-01-08
> **PAKSHAN said:**
> In computer networking, a **workgroup** is a collection of computers on a [local area network (LAN)]("http://compnetworking.about.com/library/glossary/bldef-lan.htm") that share common resources and responsibilities. Workgroups provide easy sharing of files, printers and other network resources. Being a [peer-to-peer (P2P)]("http://compnetworking.about.com/library/glossary/bldef-p2p.htm") network design, each workgroup computer may both share and access resources if configured to do so. The Microsoft Windows family of operating systems supports assigning of computers to named workgroups. Macintosh networks offer a similiar capability through the use of **AppleTalk zones**. The Open Source software package [Samba]("http://compnetworking.about.com/library/weekly/aa062499.htm") allows Unix and Linux systems to join existing Windows workgroups. 
 
===============================================
[LIMS Software]("http://labface.com/suppliers/LIMS-Software-33")
[affiliate guide]("http://www.affiliateleap.com/")
 
[SIZE=3]Thanks for the new information is also a good explanation ...[/SIZE]
[SIZE=3]But if you are a user in a network Clint-server (Domine) ....?? What can I do??[/SIZE]

---

### Post by 0863588 on 2010-01-08
> **Morbius1 said:**
> To restart the samba service:
 
Open **Terminal**
Type **sudo service samba restart**
 [SIZE=3]Thanks for the new information ...[/SIZE]

---

