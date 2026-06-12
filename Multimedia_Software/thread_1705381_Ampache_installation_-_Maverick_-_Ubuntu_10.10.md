---
title: "Ampache installation - Maverick - Ubuntu 10.10"
date: 2011-03-12
forum: Multimedia Software
---

### Post by kamelie1706 on 2011-03-12
Hi,

I have just tried to install ampache server following the tutorial:
[https://help.ubuntu.com/community/ampache](https://help.ubuntu.com/community/ampache)

When I go thought the following:
```
sudo apt-get install ampache mysql-server-5.0 phpmyadmin
```

It seems the installation does not go to the end:
```
Creating config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  done.
dbconfig-common: flushing administrative password
 * Reloading web server config apache2                                   [ OK ] 
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libgdk_pixbuf_xlib.so.2 is not a symbolic link
```


Link to [http://localhost/ampache](http://localhost/ampache) does not work.

Link to [http://localhost/](http://localhost/) shows
```
**It works!**

 This is the default web page for this server.
 The web server software is running but no content has been added, yet.

```

Any idea how I should proceed?

Thanks,

---

### Post by kamelie1706 on 2011-03-12
I have installed the missing library but the link to apache was not there.

I have added the following 
sudo ln -s /usr/share/ampache/www/ /var/www/ampache

Is the correct way to proceed?

---

### Post by trix_05 on 2011-03-16
Thanks for this, was having the same problem. I created the link as you posted and it resolved my problem!

Cheers,
TB.

---

### Post by nymusicman on 2012-06-16
See this [thread]("http://ampache.org/forums/viewtopic.php?f=2&t=3684#p17305") for the proper way, but nice work around!

---

