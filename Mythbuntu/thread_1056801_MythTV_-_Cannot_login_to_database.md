---
title: "MythTV - Cannot login to database?"
date: 2009-02-01
forum: Mythbuntu
---

### Post by Sershy on 2009-02-01
Hello

I just installed MythTV on a Ubuntu 8.04 64-bits, but when I try to run the backend setup I get an error saying "Cannot login to database?". I have no idea what to do, and I haven't found the answer googling either.

---

### Post by ianhaycox on 2009-02-01
Try this:

```

$ source /etc/mythtv/mysql.txt
$ mysql -u$DBUserName -p$DBPassword $DBName

```

and see if it connects to the database or report any errors back.

---

### Post by Sershy on 2009-02-01
When I type the Mysql command in the console I get an error saying "Error 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)"

---

### Post by ianhaycox on 2009-02-01
Looks like your password is wrong, hopefully following this should fix it

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

You may need to restart mysql and/or mythtvbackend once the password is reset.

You may have guessed but the password is in /etc/mythtv/mysql.txt so you can hack that and mysql by hand if you like.

---

### Post by Sershy on 2009-02-01
My password is correct according to the mysql.txt, but I still get an error.

---

### Post by ryansebiz on 2009-02-22
I'm having the same problem.

How do you open mysql.txt?

---

### Post by ianhaycox on 2009-02-22
```

$ sudo gedit /etc/mythtv/mysql.txt

```

---

