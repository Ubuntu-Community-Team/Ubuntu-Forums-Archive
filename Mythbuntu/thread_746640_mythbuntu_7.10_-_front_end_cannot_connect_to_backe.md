---
title: "mythbuntu 7.10 - front end cannot connect to backend !!"
date: 2008-04-05
forum: Mythbuntu
---

### Post by agent5150 on 2008-04-05
I just finished installing mythbuntu 7.10 and chose Advance setup option and provided a password for mysql.

Then I put that password in the General setup of mythtv front end.   I did that because the front end was complaining of not connecting to backend.

Even with putting the password I gave during setup... front end still complains.  I have tried different usernames (mythtv, root, my_username) with that password without success.

using root and mysql password from the setup works as mythtv-setup launches fine (connects to the db)

How do I change/add/ user mythtv to mythconverg db.
looked in the mythbuntu setup it shows mysql username etc greyed out.

thanks in advance.

---

### Post by volkswagner on 2008-04-06
Mysql does not know the new password.  You will need to tell mysql the new password.

Even if the following file shows the correct password, you will need to tell mysql.

Check file, /etc/mythtv/mysql.txt.

Then change the password for mythtv user in mysql.

```
mysql -u root -p
```

enter root mysql password, and you will now have a >mysql prompt.
```

mysql> update user set password=PASSWORD("NEWPASSWORD") where User='mythtv';
```

Edit the above line change NEWPASSWORD with your password for mythtv user.



```
mysql> flush privileges;
```
```
mysql> quit
```

See also post #4 here to reconfigure as needed.
[http://ubuntuforums.org/showthread.php?t=600315&highlight=backend+mysql]("http://ubuntuforums.org/showthread.php?t=600315&highlight=backend+mysql")

Now verify you can access mysql with mythtv user.

```
mysql -u mythtv -p
```

Your new password shall work

---

### Post by Cyborg28 on 2008-04-10
> **agent5150 said:**
> I just finished installing mythbuntu 7.10 and chose Advance setup option and provided a password for mysql.


Hi Agent,

I'm having similar problems with a basic install, no advanced options.  Have you tried a basic install (standalone back and front end)?  Any luck?
*edit* also can you run backend setup or mythtv config?  When I try I get sent to the login screen, only to log back in to the front end & repeat ad nauseum.

:confused:Cyborg28

---

