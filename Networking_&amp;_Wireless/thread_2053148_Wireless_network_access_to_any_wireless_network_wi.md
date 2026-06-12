---
title: "Wireless network access to any wireless network without a password for any user"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by d3xt3r01 on 2012-09-04
Hi people,

Just like the title says: 

Wireless network access to any wireless network without a password for any user but without giving that user administrative privileges.

In short, I'm interested to allow any user on my laptop to connect to any desired networks but not give him administrative privileges.
I've googled with no success.  I thought maybe I should add them to some groups but can't figure out which ( besides sudo ! )

Or, 2nd choice, add all users to a custom group and for that group allow those users to execute as root certain commands, but can't figure out which commands the network manager needs when the 'authenticate' window pops up..

any ideas ?

---

### Post by d3xt3r01 on 2012-09-07
I think I got it .. let me know if I'm doing this wrong:

Creat group: admin
Add all users to the admin group
Delete admin group line from sudoers !

Results
Users can connect to any wifi
Users can't use sudo to do stuff

---

### Post by d3xt3r01 on 2012-09-07
Just noticed the problem, the users can now add others users with administrator rights .. Hmmm, seems I need to figure out another way of allowing users only do wifi stuff and nothing else ! :|

---

