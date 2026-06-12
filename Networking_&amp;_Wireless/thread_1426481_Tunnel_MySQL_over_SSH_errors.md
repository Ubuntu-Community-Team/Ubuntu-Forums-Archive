---
title: "Tunnel MySQL over SSH errors"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Krijk on 2010-03-10
I'm trying to connect to a remote MySQL webserver over a SSH tunnel. I created the tunnel (with key-authentication) using:

```
ssh -f -L 3307:localhost:3306 user@www.myserver.com -N
```

When I try to connect to the server with a Python-script I keep getting connection errors.

```
OperationalError: (OperationalError) (1045, "Access denied for user 'dbuser'@'localhost' (using password: YES)") None None
```


The dbuser has 'dbuser'@'%' rights on the database and I can logon from the cli. When I try connecting to a local database (on port 3306) everything works fine, so it is obviously an SSH tunnel error. 

I've fiddled with it for some time, but I'm not getting anywhere. Any suggestions?

---

### Post by Krijk on 2010-03-10
solved. see [http://ubuntuforums.org/showthread.php?p=8946130#post8946130](http://ubuntuforums.org/showthread.php?p=8946130#post8946130)

---

