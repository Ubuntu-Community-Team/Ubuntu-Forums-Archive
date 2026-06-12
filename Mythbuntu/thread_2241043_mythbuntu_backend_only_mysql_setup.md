---
title: "mythbuntu backend only mysql setup?"
date: 2014-08-23
forum: Mythbuntu
---

### Post by matt_garman on 2014-08-23
I just did a ***backend only*** install of Mythbuntu 14.04.1 amd64.  It appears that the install/setup program does not create the necessary permissions for another system (i.e. frontend) to connect to the mysql database.

What do I need to do on my backend's mysql config so that my frontend only can actually connect?  I changed the bind-address param in my backend's /etc/mysql/my.cnf from 127.0.0.1 to the backend's external IP, and restarted mysql.

But the frontend still cannot connect.  In fact, from another machine, if I do "mysql -h <backend ip> -uroot -p", and enter the password, I get 

ERROR 1045 (28000): Access denied for user 'root'@'<frontend ip>' (using password: YES)

However, I *can* do "mysql -uroot -p" and enter the password on the backend itself.  I.e., I know I have the right password.

Seems to me specifying "backend only" setup ought to auto-magically configure mysql correctly.

Am I missing something?

---

### Post by matt_garman on 2014-08-23
I ***think*** I figured it out.  Looks like everything ***is*** indeed setup to work out-of-the-box.  I just needed the right username and password, which can be found in /etc/mythtv/config.xml (on the backend of course).  Presumably the default username is always **mythtv** and the password is auto-generated to something random (between the <Password> tags).

---

### Post by mogdad on 2014-08-25
I've had problems with mysql login using mythtv and the only thing that seemed to work was not having a password set for root on mysql (i.e. just pressing enter when it offers you to set a password). Not great for security though.

---

