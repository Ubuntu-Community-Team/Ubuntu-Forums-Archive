---
title: "Mythbuntu Repair"
date: 2008-02-08
forum: Mythbuntu
---

### Post by stoive on 2008-02-08
I want to do a repair installation, my mythweb has stopped connecting to the backend, my myth box doesn't show up in my network neighbourhood even though I can connect to it, and now, when the box starts up it goes to a database setup and goes back to the desktop without starting the front end.

So I have a few issues, I would like to do a repair installation if that is possible, but my googling has been a bit fruitless.

Can anyone explain how to do it ? ALA windows repair (keep old settings/files(media) but repair the core OS)

---

### Post by volkswagner on 2008-02-09
You can do this if you set up separate partitions for, /, /home, /var/mythtv prior to install.  This will allow you to keep media and any settings stored in /home.  I am not sure about added applications post install.  You can also create backups for specific myth settings although this may keep your errors.

I am sure someone with more knowledge will chime in with more accurate steps to help.

Your situation may be solved otherwise by repairing mysql.  Check all mythtv logs.

```
mysqlcheck --auto-repair -A -u mythtv -pmysqlpass
```

Edit "-pmysqlpass" and replace "mysqlpass" with mythtv user password for mysql.

Running the above will automatically repair and tell you what was repaired.

Make sure you can access mysql with user name mythtv.

```
mysql -u mythtv -p
```

Iif you cant access mysql, or changed password.

> When you installed, did you set a root mysql password? If so, you need to
Code:
```

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common
```


Did you change your mysql mythtv password? If so you need to
Code:
```

sudo dpkg-reconfigure mythtv-common
```


If you still can't access mysql you may need to tell it your password.  Since mythtv does not change the mysql password.

---

