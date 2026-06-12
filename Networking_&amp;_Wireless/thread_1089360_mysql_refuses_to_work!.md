---
title: "mysql refuses to work!"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by drunkmatador on 2009-03-07
I'm starting to learn how to use MySQL and right off the bat having trouble. Not with the code but just with getting the program to work!


```
mozzles@mozzles-laptop:~$ mysql start
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'start'
mozzles@mozzles-laptop:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
mozzles@mozzles-laptop:~$ 

```

I've tried running a couple other scripts I can find using a search, too.. with no luck at all. I don't have the internet at the place where I'm staying so it's really frustrating.

Any help would be appreciated, folks. Thanks. :)

---

### Post by drunkmatador on 2009-03-07
I just re-installed it and am getting the same error.. hmm.

---

### Post by albandy on 2009-03-07
mysql -u root -p

---

### Post by d_in_Conduct on 2009-03-08
You should be able to get in using:
mysql -uroot
(I've always done it with no space and no -p but try different combinations if my way doesn't work.)

Then you can create a user with:
create user <'username with single quotes'> identified by <'password with single quotes'>;

Leave out the brackets, don't forget the semicolon at the end.  You can also use:
create user 'username'@'localhost' identified by 'password';
You can use the host name 'localhost' here or a host name of your own.

Getting MySQL set up is always a struggle for me.  Sometimes it helps to reboot when you think you've done everything right.

---

