---
title: "Can't find Apache Server"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-07-13
I've got Ubuntu server installed which configures Apache automatically.  I also have Samba installed.  The server is on my home linksys network.

For some reason, I cannot access the Apache server by typing in:
[http://localhost/](http://localhost/) from any other browser except the one on the server itself.

This used to work a couple of weeks ago.  I could access the server from my windows machine using Firefox.  

What am I doing wrong???

---

### Post by zoon_unit on 2006-07-13
I can see my windows network from the Ubuntu desktop, and even access shared files, but I can't see the Ubuntu server from my Windows machine.

Is there a place in Ubuntu to choose a workgroup so the Windows network will see it?

---

### Post by DarthMandeep on 2006-07-13
Do you have a firewall of some kind installed on Ubuntu?

If you're using Firestarter, go to the preferences section, find the advanced tab, and de-select the "Block broadcasts from external networks" option.

You should check your apache conf files to see if you're limiting access to the localhost.

---

### Post by zoon_unit on 2006-07-13
Well, I'm making some progress.  I can access the Linux Apache server from the Windows Firefox by typing in my local Linux server name (not localhost)  Duh!

I can also search for the server by name in Windows network places and the local server name comes up, but I can't actually access it because windows asks for a name and password.  I type in my Linux user name and password but that doesn't work.  Any ideas??

My apologies for being such a Linux newbie, but I gotta start somewhere!  :-)

---

### Post by tturrisi on 2006-07-13
To access www content on the box that apache is installed on, type in the browser address bar:  [http://localhost/](http://localhost/)
To access www content from OTHER computers on the LAN type in the browser address bar the ip address of the server box:  [http://192.168.1.xx](http://192.168.1.xx)  or what ever the address is.  Some routers use 192.168.0.x.

---

