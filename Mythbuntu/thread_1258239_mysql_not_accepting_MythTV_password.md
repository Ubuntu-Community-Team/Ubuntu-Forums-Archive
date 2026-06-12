---
title: "mysql not accepting MythTV password"
date: 2009-09-04
forum: Mythbuntu
---

### Post by colinnwn on 2009-09-04
Hi all,

I'm trying to add the Live TV idle timeout setting to my MythTV database.

I looked in /etc/mythtv/mysql.txt to find my mysql password for the user mythtv. Then I did a -

```
mysql -u mythtv -p mythconverg
Enter password: <password entered here minding case>
ERROR 1044 (42000): Access denied for user 'mythtv'@'localhost' to database 'mythconverge'
```

Can anyone tell me what I am doing wrong?

Thanks.

---

### Post by frego on 2009-09-05
Maybe try to leave off the db:

```
mysql -u mythtv -p
``` 

enter your password and then do a:
```
use mythconverge;
```

If the mythtv user can't access the db then it's a permission issue.

---

### Post by jb5 on 2009-09-06
Something else that might be worth trying is to run the command from a root shell.```
sudo su
```
Doesn't answer your question, but might at least get you to where you want to go.

---

### Post by colinnwn on 2009-09-10
Thanks frego,

I did what you suggested and it worked. Then I tried the way I originally learned, using mythconverg, rather than mythconverge, and it worked too. 

I thought I was careful to try both ways, and to copy and paste right out of the command line I was having problems in. But perhaps I was distracted and messed up.

---

