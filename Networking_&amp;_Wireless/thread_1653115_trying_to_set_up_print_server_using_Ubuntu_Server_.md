---
title: "trying to set up print server using Ubuntu Server 10.10"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by rogdawg on 2010-12-26
Hi all,

I am trying to set up a print and file server for my home network using Ubuntu Server. The file server part of the task seems to working well. I can see the shared directories from my Macbook and my wife's Windows Laptop. I am stuck on the printer setup, though. 

I have an HP Photosmart printer connected to the Ubuntu Server machine via USB cable. I have confirmed that CUPS is running on the server. [I enter "sudo restart cups" and get "cups start/running, process 2129"]. Samba is running properly, because the file sharing seems to be working. I assume that I have to add the printer somehow but, I haven't found anything on the web that tells how to do that. 

Here is the relevant information from the file at /etc/samba/smb.conf:
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   printer admin = root
   public = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

I suspect that I am almost to my goal. I just have to figure out how to add a printer on the Ubuntu Server machine. 

I appreciate any advice anyone can give. 

Thanks!

Well the more I research this, the more I realize I am in over my head. I will need to install the drivers somehow, add the printer somehow, then share the printer somehow, then connect from the other machines in on the "network" somehow. Ummmm. I think I will stick with what I have, and just plug the printer into whichever laptop needs to print, then print. It's the cowards way out, but its infinitely easier.

---

