---
title: "MySQL password"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-07-13
I installed the Ubuntu server edition which installs and configures LAMP automatically.  I've now installed PHPMyAdmin to administer MySQL databases.

However, since Ubuntu set everything up, I have no idea what my MySQL login and password is.  I've read where I can access this in the "command and control center" but I have no idea how to access this.

Help!

---

### Post by jaredvolkl on 2006-07-14
By default I think root has a blank password. I just found this myself. Try this:

mysqladmin -u root password "password_you_wish_to_set"

---

### Post by quedigg on 2006-07-15
yes , by default Mysql generates an empty password for the root .

however, type(in terminal) ```
sudo less /etc/mysql/debian.cnf
```

the maintaince account is there ,as well as the sock file path.

note :
i think you should install Mysql (version 5)from synaptic, it's not install by default ,i think so .


Thanks

---

