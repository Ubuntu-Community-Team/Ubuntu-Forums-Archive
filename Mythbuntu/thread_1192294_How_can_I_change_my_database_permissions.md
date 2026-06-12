---
title: "How can I change my database permissions?"
date: 2009-06-19
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-19
Hi all,

I need to change access to permissions to my MythTV database so that a front end application for XBMC can get the data. phpmyadmin was suggested but honestly I have no idea how to use it...I installed it like so:

> sudo apt-get install phpmyadmin

...but I cannot even figure out to run it (I'm kind of embarrassed lol). The mysql command line client was also suggested but again I have no idea.

Can some one please suggest a simple way to go about doing what I want, and possibly point me to a good example as well?

Any help would be greatly appreciated.

EDIT:

To give you some background I am using a XBMC plugin called MythBox. When I run it I get the following error:
> 
connect to mysql failed: (1045, "access denied for user 'mythtv'@'localhost' (using password: yes)") 

- Matt.

EDIT EDIT:

I've just realised how noob I really am. Apparently I should have a web server running and everything. During the install it asked me what type I wanted and I checked "apache" as it sounded familiar, and then another question came up and I answered "no" for some damn reason.

I can't find any reference on my system suggesting it is even installed, and even then a google search has not helped me at all. Even if I ahd it running I have no idea what to do!

:confused:

---

### Post by Mattaus on 2009-06-20
Ok, so I've been reading my **** off and have come across this method, but I won't want to try it until someone who knows what they are doing can confirm:

> mattaus@HTPC:~$ sudo mysql

mysql> show databases;

+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
| mythconverg        | 
+--------------------+
3 rows in set (0.00 sec)

mysql> USE mysql;

mysql> SHOW TABLES;

+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| columns_priv              | 
| db                        | 
| func                      | 
| help_category             | 
| help_keyword              | 
| help_relation             | 
| help_topic                | 
| host                      | 
| proc                      | 
| procs_priv                | 
| tables_priv               | 
| time_zone                 | 
| time_zone_leap_second     | 
| time_zone_name            | 
| time_zone_transition      | 
| time_zone_transition_type | 
| user                      | 
+---------------------------+
17 rows in set (0.00 sec)


So I know I have a database called **mythconverg**, and a user profile...

Can I add the permissions for mythtv@localhost by doing the following:

> mysql> INSERT INTO user (Host, User, Password, Select_priv) VALUES (' ', 'mythtv@localhost', password('mythtvpassword'), 'Y');
mysql> FLUSH PRIVILEGES;   
mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO mythtv@localhost;
mysql> FLUSH PRIVILEGES;

Or would this be better:

> mysql> grant usage on *.* to mythtv@localhost identified by 'mythtvpassword';
mysql> grant all privileges on mythconverg.* to mythtv@localhost;

As you can tell to someone like me they both seem to do the same thing - namely give the user access and all privileges.

I'm so lost :lolflag:

---

### Post by Mattaus on 2009-06-21
Can anyone shed some light on this? I managed to trash all my permissions and could not restore or replace the database so I had to wipe the Hard Drive and start from scratch :(

Thankfully I've just got into the habit of taking system snap shots often so it was a relatively painless task, but still I'd rather avoid making the same mistake again.

---

