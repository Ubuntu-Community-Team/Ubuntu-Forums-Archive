---
title: "Set up ftp on /var/www???"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by psyllex on 2013-03-16
Hello people!  I setup the ftp server from the repository using vsftpd.  

I did:  ```
chown -R <username> /var/www
```
additionally: ```
usermod -d /var/www ftp
```

But I still can't ftp into www which is useless for trying to do any kind of programming on my web server.  Does anyone know how I can get permissions on /var/www?

---

### Post by psyllex on 2013-03-16
Oh damn...nevermind....lol.  I didn't actually do a chown -R on /var/www/  just /var/www....

Man you guys are awesome you helped me out without even responding to my thread!

---

