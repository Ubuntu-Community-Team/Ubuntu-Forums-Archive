---
title: "No MySQL, did it install?"
date: 2008-05-19
forum: Mythbuntu
---

### Post by ZippyP on 2008-05-19
Hi

:confused:
I'm a newbie to this. I installed MythTv into Ubuntu via the Internet. Well, I thought the install went fine until I found that when in the MySql access (2nd step after selecting a language) it would not connect. I don't know if No UPnP backends found means anything, but I'm stuck at the MySQL login. I looked at the folders and made it to the etc/MythTV/MySQL folder and there is only two files in it, and they are both folders. I have a server running an Internet Radio station, and I know that I have more than that in the MySQL directory. In laymen's terms, until I understand what went wrong during the install, can someone help with this situation? Apparently there is a MySQL. txt file, but I don't think MySQL is running or even installed.
I have been at this all weekend with Linux, Ubuntu and MySQL books all around me. I can't seem to beat this. Any help would be greatly appreciated.

Thanks

---

### Post by volkswagner on 2008-05-19
This is not uncommon.

Take a look here.  

[http://ubuntuforums.org/showthread.php?t=790814&highlight=mythconverg]("http://ubuntuforums.org/showthread.php?t=790814&highlight=mythconverg")


or here

[http://ubuntuforums.org/showthread.php?t=779326&highlight=mythconverg]("http://ubuntuforums.org/showthread.php?t=779326&highlight=mythconverg")

You want to make sure you can log into mysql.  If you did not set a root password it shall be blank.

```
mysql -u root
```

If you did set a password

```
mysql -u root -p
```

---

### Post by ZippyP on 2008-05-19
Hello Volkswagner

Thanks for the response.
If I type [COLOR="Red"]**mysql -u root -p[/COLOR]**
I get the password prompt and what ever I put in the correct password or the wrong password I get this response.
**Can't connect to local MySQL server through socket '/var/run/mysqld.sock'(2)**
Where is MySQL and its database hidden at?  I can't seem to find it even turning off the hidden files.  It almost looks to me it never installed.  I guess there is no way of going back and trying to install it again via the web page since it states that the files are already installed. I tried the command line advice from the links, still no go.  I can usually beat amy situation with software but this one has me beat so far.:confused:

Thanks

---

### Post by volkswagner on 2008-05-19
This thread is specific to your problem.  Read through it before changing anything.

One person had a real simple one, installed mysql-client not mysql-server.

[http://ubuntuforums.org/showthread.php?t=276470&page=2]("http://ubuntuforums.org/showthread.php?t=276470&page=2")

---

### Post by ZippyP on 2008-05-19
Hi

Yikes....  Which suggestion do I follow in that thread?  Everyone has a different suggestion on fixing the problem.  One suggestion was uninstalling and reinstalling, I guess was Ubuntu or MythTV.  This would not be a problem since both packages install pretty fast, but what would keep it from not doing the same thing over again?  It looks as if after doing a manual MySQL server install, they came up with another problem.  I wonder if I should just wait until there is a fix.

Thanks again.

[COLOR="Red"]**Update...Day Two**[/COLOR]I installed MySQL server via the MythBuntu Alternate disk.  As I suspected MySQL server was not installed when using the Internet install of MythTV.  I am still at the point where MythTV does not log   into MySQL.  Is there a easy to follow Step by Step fix for this? As stated above everyone is giving their version of a fix, and so far none is working here.

[COLOR="Red"]**Update...Day Three**[/COLOR]
I followed everything I could find and still the message "[COLOR="Red"]**No UPnP backends found**[/COLOR]" and then no login to MySQL.  Three days later and still no go.  I'm not going to let this beat me. What a pain backside just to enjoy TV.

[COLOR="Red"]**Update...Day Four**[/COLOR]
I can connect to MySQL by typing [COLOR="Red"]mysql[/COLOR] in terminal mode
Typed [COLOR="Red"]\h [/COLOR]and got the help list. Typed [COLOR="Red"]\s[/COLOR] and got a working status typed [COLOR="Red"]connect[/COLOR] and got this
[COLOR="Red"][B]ID: 18440
Current Database: ***None***[/B][/COLOR]
What is up with this? ](*,)
Anyone Else?

[COLOR="Red"]**Update...Day Five**[/COLOR]
Took time out from the box to clear head

[COLOR="Red"]**Update...Day Six**[/COLOR]
Fixed???  Installed MySQL Admin, everything looked OK with MySQL Admin, reentered the password, started MythTV and it made it past the SQL logon. After installing or maybe reinstalling the server two days ago and installing MySQL Administrator today, this is something I should have done at day one of this fun filled trip ;) through MythTV.
New...Could not connect to the master backend server...?
Thanks again Volkswagner for pointing me in the right direction for the MySQL database.
[COLOR="Red"]**All Fixed...**[/COLOR]Well, almost... ):P

---

