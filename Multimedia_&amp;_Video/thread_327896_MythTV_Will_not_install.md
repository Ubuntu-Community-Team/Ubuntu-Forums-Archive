---
title: "MythTV Will not install"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by MetalSlugX on 2006-12-29
here is what I keep getting when I try to install MythTV

Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mythtv-frontend (0.20-0.2ubuntu2) ...

Setting up mythtv-backend (0.20-0.2ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Setting up mythtv-themes (0.20-0.1) ...
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help here? I'm trying to follow a guide at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) but it will not work no matter what I try.

---

### Post by deadgobby on 2006-12-30
[https://help.ubuntu.com/community/MythTV_Dapper_Frontend](https://help.ubuntu.com/community/MythTV_Dapper_Frontend)
Gobby

---

### Post by MetalSlugX on 2006-12-30
I followed that edgy version of the guide you linked me to after I completely removed MySQL server and I removed MythTV then tried reinstalling it. I keep getting the exact same error. I tired dpkg-reconfigure --force mythtv-database but that didn't do anything. But I'm not sure I did it right. I'm totally lost here.

---

### Post by kevin_hill54 on 2007-01-01
Hi

I've just spent the last 3 days trying to figure out how this all works.

I continue to have a problem with Mysql database not having correct user name or not conected. I have removed both Myth and Mysql many times. I have followed the Ubuntu help instructions the [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) instructions the [http://lists.samba.org/archive/linux/2006-November/016496.html](http://lists.samba.org/archive/linux/2006-November/016496.html) and [http://prettymad.net/articles/how_to_build_a_myth_tv_box2](http://prettymad.net/articles/how_to_build_a_myth_tv_box2). I am so confused that I am about to give up.

I am sure I have stuffed something up but have no idea what I have done.

Is there anywhere else to go as there seems to be a problem with the Mysql database link.

This doesn't help but makes me feel better that someone else knows that these problems are happening to others.

Thanks

---

### Post by michas_u on 2007-01-03
I have the same Problem....

Has anyone a resolution????

Thanks

---

### Post by majoridiot on 2007-01-03
i made the initial mistake of following too many guides with conflicting info that tended to
mess things up more than anything.  i eventually sussed it all myself, but in the meantime
some great ubuntu mythtv guides and packages were put together.

on my last backend build from scratch, i collected my notes and gave the guide a shot... and
had a working backend up and running from a new install in less than an hour.  do yourselves
a favor- uninstall and COMPLETELY REMOVE your installed mythtv packages, make sure the
.mythtv hidden directory in your home (or mythtv home) directory is deleted and follow along
with this guide.

[https://help.ubuntu.com/community/MythTV?highlight=%28mythtv%29](https://help.ubuntu.com/community/MythTV?highlight=%28mythtv%29)

---

### Post by tagra123 on 2007-01-03
> **majoridiot said:**
> i made the initial mistake of following too many guides with conflicting info that tended to
mess things up more than anything.  i eventually sussed it all myself, but in the meantime
some great ubuntu mythtv guides and packages were put together.

on my last backend build from scratch, i collected my notes and gave the guide a shot... and
had a working backend up and running from a new install in less than an hour.  do yourselves
a favor- uninstall and COMPLETELY REMOVE your installed mythtv packages, make sure the
.mythtv hidden directory in your home (or mythtv home) directory is deleted and follow along
with this guide.

[https://help.ubuntu.com/community/MythTV?highlight=%28mythtv%29](https://help.ubuntu.com/community/MythTV?highlight=%28mythtv%29)



I agree.

Follow one guide and stick to it. Some of the guides just don't work.   By the way, to fix mysql -- sounds like a preveleges.  Try googling for mythtv mysql priveleges.  I also installed phpmyadmin. That program really lets you look at and work with a mysql database using a html browser.  Once you get it working be sure to backup the database often -- very important.  

I had a lightning strike mess up my mythbox last year and was able to get things up and running quickly by restoring my mythbox using partimage and then using the most recent backup of mythconverg.

I followed one of the guides and than had to manually fix the mysql priveleges.


the commands will look something like this for privelege, but be sure to read up first.

mysql -u root -p mythconverg
mysql> grant all on mythconverg.* to mythtv@"10.0.1.%" identified by "mythtv";
mysql> flush privileges;
mysql> quit

---

### Post by dannyboy79 on 2007-01-03
> **kevin_hill54 said:**
> Hi

I've just spent the last 3 days trying to figure out how this all works.

I continue to have a problem with Mysql database not having correct user name or not conected. I have removed both Myth and Mysql many times. I have followed the Ubuntu help instructions the [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) instructions the [http://lists.samba.org/archive/linux/2006-November/016496.html](http://lists.samba.org/archive/linux/2006-November/016496.html) and [http://prettymad.net/articles/how_to_build_a_myth_tv_box2](http://prettymad.net/articles/how_to_build_a_myth_tv_box2). I am so confused that I am about to give up.

I am sure I have stuffed something up but have no idea what I have done.

Is there anywhere else to go as there seems to be a problem with the Mysql database link.

This doesn't help but makes me feel better that someone else knows that these problems are happening to others.

Thanks

i had this same problem and no matter how many times you remove mysql it still will not get rid of the file that it stored with the root mysql password. you need to remember what you chose and do a reconfigure on the mysql root password. I was lucky and remembered that's the only way I could get out of that error, otherwise you may need to reformat and reinstall. actually I take this last statement back, check this out: [http://www.debian-administration.org/articles/442](http://www.debian-administration.org/articles/442)

apparently you can run the sql database so that it doesn't restrict which users can make changes, therefore you'll be able to reset your mysql root password even if you forgot the old one. good luck everyone.

---

### Post by majoridiot on 2007-01-03
> **dannyboy79 said:**
> i had this same problem and no matter how many times you remove mysql it still will not get rid of the file that it stored with the root mysql password... 

on my first install months and months ago, i made the mistake (one of many) of following
more than one guide and trying to fix one guide's errors from another... totally buggering
mysql more than once.  in my experience, if you remove mysql and mythdatabase with
synaptic, marking them for COMPLETE removal, then the pw probs are gone.

seriously, if it were me (because i've been there), i would do a *complete* removal of mysql
and all mythtv components and then follow one of mario's guides from the link i posted above.

---

### Post by dannyboy79 on 2007-01-04
NOPE! i did an uninstall and purge and everything in the book trying to get rid of mysql and whatnot so that I couldstop the root password error. this was even stumping Mario as he was helping me over gaim. all i can say is that despite me doing the remove, uninstall, and even a purge everytime I would reinstall and try to perform that one step it would give me that same error. so I not sure where the data was kept in my system but for some reason is was not getting flushed and like I said I was lucky to have remembered what the original password was that I entered. i guess I can't say it didn't work for you cause I don't know that but I can for sure tell others of my situation and like I said, Mario couldn't believe it either!

---

### Post by majoridiot on 2007-01-04
hm.  that *is* ODD...

---

### Post by MoebusNet on 2007-01-05
My 2 cents...

After at least 6 install attempts to include reformatting hard drive and reinstalling ubuntu/kubuntu from scratch, I have yet to get itv or mythtv to work. It just isn't ready for the average end-user yet, I guess. :(

---

### Post by tagra123 on 2007-01-07
knoppmyth might be easier

The Fedora guides work will for mythtv

I put mine on ubuntu  using breezy and have kept it on breezy

---

### Post by cfcubed on 2007-01-08
I just went through this a couple days ago...

Got the same 2 classes of errors you got (root pass prob & authentication err).

Based on other feedback here & a search I found a thread on another forum that yielded help.  As I recall I:

0) Looked at my log & could see my prob was not finding the mysql.txt file (more /var/log/mythtv/mythbackend.log)

1) got into MySQL & explicitly set my root password & the password for the mythtv user,

2) found the mysql.txt file in a .mythtv folder & set the proper/new password for the mythtv user.

3) copied that mysql.txt file into a .mythtv folder all over the place (for root user, mythtv user & my logged on user home dirs).  One problem definately was that I was still logged in as my default user.

4)  For some reason, the initial setup still got the auth protocol error.  So tried explicit sudo commands (like mythfilldatabase, mythtv-backend & then mythtv-frontend) & the front-end came up (not using indirect ways of invoking them as in some guides).

It was too tired to figure out exactly which step(s) "fixed" my problem(s), just left happy things were working:)

Good luck,
Chris

---

### Post by christooss on 2007-01-16
> christooss@ubuntu:~$ sudo mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password:NO)
christooss@ubuntu:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I get this error. When I tried some solution for problem in first post which I get to

---

### Post by Erlander on 2007-01-17
I too can't get Mythtv to work.  OK I'm new to linux.

However once I had my tuner properly installed I found that Kaffiene does most of what I want to do.

Just a thought.

I'll get back to Mythtv in time as I don't want it to beat me.

Rob

---

### Post by majoridiot on 2007-01-17
> **christooss said:**
>  christooss@ubuntu:~$ sudo mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password:NO)
christooss@ubuntu:~$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I get this error. When I tried some solution for problem in first post which I get to

you need the -p to login with a password:

```
mysql -u root -p 
```

---

### Post by AusIV4 on 2007-01-17
> **MoebusNet said:**
> My 2 cents...

After at least 6 install attempts to include reformatting hard drive and reinstalling ubuntu/kubuntu from scratch, I have yet to get itv or mythtv to work. It just isn't ready for the average end-user yet, I guess. :(
MythTV is great software, but it can take some work to get it to install. If you're *just* going to be using MythTV on the box, and not using it as a desktop, I'd recommend trying knoppmyth, as it is an entire distribution built around getting mythtv working smoothly and effortlessly.

If you must get it working Ubuntu, it is quite possible. I've done it numerous times, but I've never run into the problems people are mentioning here. As several others have said, pick a guide and stick with it. There are several different ways of installing MythTV, and some of them may not mix.

Once MythTV is installed, anyone can use it. When I have an apartment next year, I intend to install a frontend on an old Xbox or a System 76 Koala, if I can afford one.

---

### Post by christooss on 2007-01-17
> **majoridiot said:**
> you need the -p to login with a password:

```
mysql -u root -p 
```

And what is the default password. If I leave it empty it still gives me that error

---

### Post by majoridiot on 2007-01-17
> **christooss said:**
> And what is the default password. If I leave it empty it still gives me that error

from a default installation:  user:mythtv password:myth

---

### Post by christooss on 2007-01-17
$ sudo mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)

I tried myth and mythtv for pasword. And I tried with 

sudo mysql -u root -p

---

### Post by majoridiot on 2007-01-17
> **christooss said:**
> $ sudo mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)

I tried myth and mythtv for pasword. And I tried with 

sudo mysql -u root -p

how did you install mythtv and mysql?  did you follow a guide or guides?  if so, please post
links, so we can see what steps you took installing things.  that might shed light on what's going
on.

---

### Post by christooss on 2007-01-20
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Its something wrong with mysql and I cannot solve it. I tried bunch of solutions but none worked for me

---

### Post by christooss on 2007-01-20
> christooss@ubuntu:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
christooss@ubuntu:~$ sudo rm -rf /var/lib/mysql
christooss@ubuntu:~$ sudo apt-get autoremove --purge mysql-server
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti       
Reading state information... Narejeno
The following packages were automatically installed and are no longer required:
  mysql-server
Naslednji novi paketi bodo ODSTRANJENI:
  mysql-server*
0 nadgrajenih, 0 na novo name&#353;&#269;enih, 1 bo odstranjenih in 0 ne nadgrajenih.
Potrebno je dobiti 0B arhivov.
Po odpakiranju bo spro&#353;&#269;enega 69,6kB prostora na disku.
Ali &#382;elite nadaljevati [Y/n]?
(Reading database ... 121190 files and directories currently installed.)
Removing mysql-server ...
christooss@ubuntu:~$ sudo rm -rf /var/lib/mysql
christooss@ubuntu:~$ install mysql-server
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti       
Reading state information... Narejeno
Naslednji NOVI paketi bodo name&#353;&#269;eni:
  mysql-server
0 nadgrajenih, 1 na novo name&#353;&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.
Potrebno je dobiti 0B/39,5kB arhivov.
Po odpakiranju bo uporabljenega 69,6kB dodatnega prostora na disku.
Selecting previously deselected package mysql-server.
(Reading database ... 121188 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.24a-9_all.deb) ...
Setting up mysql-server (5.0.24a-9) ...
christooss@ubuntu:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


And mysqladmin -u root password my_password doesn't work to

---

### Post by majoridiot on 2007-01-20
> **christooss said:**
> [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Its something wrong with mysql and I cannot solve it. I tried bunch of solutions but none worked for me


as i recall, i followed that guide about six months ago (when it was a dapper mythtv guide) and
i never came close to getting a working myth setup.

it it were me, i would COMPLETELY remove (and purge) everything you installed from that
site and follow the most complete and accurate guide i've found for mythtv on ubuntu:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

pick which setup you want, and then follow VERY CLOSELY each step... and you should not
have any problems.  i have followed mario's guides for mythtv, ivtv and lirc setup and have
never encountered a problem.

the key is to think about each step and not skip anything.  more than half of the problems
encountered are from overlooking something important.

good luck! :D

---

### Post by christooss on 2007-01-20
Hm from that howto I just installed mythtv I got mysql installed but I have never used it.

when I was installing mythtv I got error something with wrong password, wich I never changed, for mysql database.

Please look at my previous post where I try to get in to database. Suggestion about this was in [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) howto.

And I have removed mythtv completly and mysql to. Please look at previous post.

---

