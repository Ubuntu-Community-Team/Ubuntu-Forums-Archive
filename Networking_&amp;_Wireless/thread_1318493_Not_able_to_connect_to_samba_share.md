---
title: "Not able to connect to samba share"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by Haborym on 2009-11-07
When i try connecting to my samba share. When i try to connect by clicking on "network" in nautilus i get this error message: 

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.


When i re-click i get the server listed. But when i type in the password it is not able to connect and the username and password window pop up again.

I am able to connect to the server from my Arch install on this netbook and on the arch install on my desktop computer, plus i can connect from the Windows XP install on my dekstop computer plus from my mom's laptop that has Vista installed. 

And yes, i use the same username and password on them all. It work on the other so that is not the problem. 

The server have FreeNAS installed. I use Ubuntu Netbook Remix 9,10 on this laptop, that i try to connect to the server from. 

I have googled myself into a coma so i hope someone can help.

---

### Post by Haborym on 2009-11-07
ok, i got rid of the dbus error by following what is written in this post:
[http://ubuntuforums.org/showpost.php?p=4962077&postcount=5](http://ubuntuforums.org/showpost.php?p=4962077&postcount=5)

but i still can not connect if my life depended on it.

---

### Post by jonfenton on 2009-11-11
I am having the same problem. On rebooting I find I am unable to connect to my Samba share. By deleting the password from Seahorse I can log in again. I am still stumped on a permanent solution though.

---

