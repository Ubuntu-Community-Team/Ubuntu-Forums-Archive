---
title: "Trouble with MySQL server"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-02-12
Hello everyone.  Like the title states, I am having trouble with my mysql server.  I can access and change stuff locally, but that is not what I need.  I am trying to run php scripts for updating the data, but when I try to connect, it's giving me issues with the connecting.  I know that it's not my code because I ran it on fatcow.  


I think the main issue is that the hostname is set to "localhost".  Is there any way to change that or is there anyway I can get connected to my mysql server via any script?  

-fox

---

### Post by SoftwareExplorer on 2011-02-12
So you're saying that you can't access your mysql server over the network?

I think mysql lets you specify that a username can only login from a certain IP. I think by default it's localhost only.
I usually use MySQL administrator. If you go to user administration in the sidebar, it will show user accounts. If you expand the user account it lists where that user is allowed to login from.

---

### Post by computerfox on 2011-02-12
Here's some more information.

---

### Post by computerfox on 2011-02-12
I think this is actually what you were asking me about.

---

### Post by wojox on 2011-02-12
Where is the MySQL Server and Apache2 Server located?

---

### Post by computerfox on 2011-02-12
not sure what you mean. do you mean which port?


ports: 

server: 80
webmin:666
phpmyadmin: 3360, i believe

directories:

apache2: /etc/apache2
mysql: not sure.  i know that phpmyadmin is located in /ect/phpmyadmin, i believe.

physical:
well, it's actually the same physical server.

---

### Post by computerfox on 2011-02-12
any ideas, anyone?

---

### Post by wojox on 2011-02-12
What I mean is your connecting locally through your LAN and not remotely?

---

### Post by computerfox on 2011-02-12
well, i tried both.  as you see in the pictures, the server is actually set to localhost for some reason, instead of the actual server name (foxwebhosting.dyndns.org).

---

### Post by computerfox on 2011-02-13
Anyone?

---

### Post by wojox on 2011-02-14
What does the actual error say?

---

### Post by computerfox on 2011-02-15
Oh.  Well, the server is foxwebhosting.dyndns.org.  The MySQL server says localhost.  I tried every possible combination of hostname/username to attempt to access the MySQL server with the script, but it always says "cannot connect", which either means the password/username is wrong, which i know are not, i'm using the wrong hostname(which could be possbile), or i can not access the server from script at this point.

---

### Post by computerfox on 2011-02-19
Any thoughts?

---

### Post by computerfox on 2011-03-01
does anyone have any ideas for this issue?

---

