---
title: "samba client set up"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by Jefferythewind on 2011-03-26
Hi everyone,

  I have a couple ubuntu servers running on a Windows Network, and I would like to set them up so that they appear on our windows network.  It is not super important that they show up in the windows browser, but I am hoping that setting them up like this will make the connections between Ubuntu and Windows a little faster.  

  I think I need to set up the ubuntu servers as samba clients, and I have installed samba on one of the servers, following this tutorial -> [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html#windows-networking-clients]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html#windows-networking-clients").  However when I try to restart samba using /etc/init.d/samba restart it gives me a "command not found error".  I found there is a command to restart using /etc/init.d/smbd/ restart.  Is this the same thing?

  I would appreciate help to this question and any other advice about setting this up.  Also any information about slow connections between linux and windows.  Thanks

---

### Post by Doug S on 2011-03-26
Note: I am not a Samba expert. January was the first time I ever installed and used samba on my own system (even though I have wanted to for years). However, I have been a linux users for about 15 years.
 
I used the Ubuntu server guide for version 10.10 as my reference. To restart samba after making changes I use these commands:
 
sudo restart smbd
sudo restart nmbd
 
On my system, I did have some troubles with authentication of users and such, but did get it sorted out in the end. Now each user has access to both a private share and a public share on my Ubuntu server. Each user has mapped those drives to their windows machines. Perfromance has been great.

---

### Post by Jefferythewind on 2011-05-07
Thanks Doug for the help.

Actually I found the speed problem.  The speed problem that I was experiencing was in the mysql connections.  Since the ubuntu boxes were on the windows DNS, the DNS wasn't figuring out their names from the IP addresses.  MySql has a setting to disable resolve client names when connecting.  This way it just uses the IP address to make connections.  When I disabled the name resolving then the speed came back.  So it wasn't a samba problem to begin with.

Thanks everyone!

---

