---
title: "apache error.. cant stop the server"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2010-01-07
this is the error im getting

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

i get that error when  try to run the following code

```
/etc/init.d/apache2 stop
```

it used to work just fine, i would be able to restart, stop, or start the apache server.. 

i checked my logs and it seems that some IPs from china and korea were exploring my web server and now i dunno whats goin on...

i tried googling the error but those results arent really helping
any ideas??

---

### Post by puppywhacker on 2010-01-07
use
```
sudo /etc/init.d/apache2 stop
```

The warning your getting should be harmless, if it doesn't stop your apache server you can kill it, by finding it's process-id (pid) it's the left top number in the collumn by itself and kill it

```
sudo pstree -p | grep apache
sudo kill <pid>
```

run the pstree again and if it isn't empty after 30 seconds, use 
```
sudo kill -KILL <pid>
```
to get it down without going through the shutdown routine and abort.

---

### Post by gfunkera on 2010-01-07
SUDO! i keep forgetting about that! thanks man!

---

