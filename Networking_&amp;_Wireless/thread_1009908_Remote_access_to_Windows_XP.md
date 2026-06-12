---
title: "Remote access to Windows XP"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by seagull1 on 2008-12-13
Hi I am trying to remotely access a PC  which has 
Windows XP. 
Currently I am using Ubuntu 8.10
Once I login, I get a shortcut for the Windows XP desktop and when I click on it, it should open a Remote desktop application. But I get an error message "This terminal session is not supported on your computer"...
Any help is much appreciated.
Thanks

---

### Post by bluefrog on 2008-12-13
apps/internet/"terminal server client" not "remote desktop".

---

### Post by seagull1 on 2008-12-13
Yes you are correct ...apps/internet/"terminal server client" not "remote desktop". How can I fix that. many thanks

---

### Post by seagull1 on 2008-12-13
How can I manage, that clicking the shortcut will open up the Ubuntu Terminal Server Client, instead of looking for a Windows terminal server client?

---

### Post by superprash2003 on 2008-12-13
you want to remote control a windows xp machine from ubuntu via LAN?

---

### Post by seagull1 on 2008-12-15
No, to remote control a windows xp machine from ubuntu via WAN using Application Secure Gateaway. Do I need to Install   Juniper Networks, Inc. on Ubuntu 8.10 as I use to have it on my old windows vista in order to 
to remote control the windows xp. 
How can I resolve now the issue with the following error message on my Ubuntu 8.10 "This terminal session is not supported on your computer"

Thanks

---

### Post by seagull1 on 2008-12-15
I am able to establish a secure ASG session from my Ubuntu and then I am able to view the shortcut "My desktop" for my Window XP machine, however once I click on it the following message will pop up.
"The terminal session is not supported on your computer."

---

### Post by seagull1 on 2008-12-15
In other words...    The ASG will launch a process  that will attempt a RDP  connection to a loop back IP address (127.x.x.x) this is then port forwarded back  to the ASG inside an SSL tunnel.
Is it possible  that the Connections to loop back IP addresses may be blocked by a personal firewall or Ubuntu do not support multiple loop back addresses?

---

### Post by seagull1 on 2008-12-15
Any thoughts or ideas? 
Thanks

---

