---
title: "Printer sharing via samba/cups"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by sasherm13 on 2006-06-03
Okay, I am real n00b and need some help.  I just switched from XP to Dapper on my desktop but kept XP on my laptop due to school needs.  My printer is attached to the Dapper box and I want to shar the printer on my network so I can print from my XP laptop to my printer hooked to my Dapper box.  I have searched the web and tried to get this to work, but I keep hitting walls.  Could someone break this down into small pieces that I can understand?  

I have it such that my XP laptop can see the printer on the network as a share, btu I have not been sucessful in installing the network printer.

Someone please help a desperate n00b.

---

### Post by sasherm13 on 2006-06-04
Please help, I need this working soon or I will have to switch back to XP :(

---

### Post by breshead on 2006-06-20
[QUOTE=sasherm13]Please help, I need this working soon or I will have to switch back to XP :([/QUOTE]

sudo apt-get install samba
(If you are asked for password, enter your own users password)

sudo vi /etc/samba/smb.conf

OK, I just realized this is probably already documented...

Here is the general samba section, if you dont want to have to log in to use samba then do this.
[http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29]("http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29")

Here is the printer section
[http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba]("http://ubuntuguide.org/wiki/Dapper#How_to_print_on_remote_Ubuntu_machine_via_samba")

Hope this helps...

---

