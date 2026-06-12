---
title: "freeradius help"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by justinede on 2008-12-13
Hello I am trying to set up a radius server using this guide: [http://www.keller.com/wifi/CNIT107HW7.html](http://www.keller.com/wifi/CNIT107HW7.html)

and i downloaded freeradius from the website and extracted it and did all the steps up untill #make install. This is where is ran into a problem. It says it needs to put something in usr/local/etc but it dosnt have permission and i realized that even I, the admisitrator cant put or edit anything in my filesystem.. I need help. I am a linux nub.

Thanks,
Justin

---

### Post by Ett_tingest on 2009-10-22
If you are using Ubuntu Desktop youre not admin.
The root is the one having administrative rights in all directories.
But since the root is locked down in Ubuntu due to security reason (thats my theory anyway) you have to use the command "sudo" which enables you to do things that only root normally would be able to do. First time you use this command it will ask you for the password for root access. That is the same password as you have for your own account if I have understood it correctly? 
 
for example if you want to download php5 to your dist you write
 
"sudo apt-get install php5"
 
I´ve followed another guide which ive had some problems with since i cant find a script i need in daloradius-0.9-7 which i need for MySQL.
Maybe you can help me with that?

/var/www/daloradius-x.y-z/contrib/db/fr2-mysql-daloradius-and-freeradius.sql

thats the script i need.
The tutorial im following is: [http://ubuntuforums.org/showthread.php?p=8126395](http://ubuntuforums.org/showthread.php?p=8126395)

---

