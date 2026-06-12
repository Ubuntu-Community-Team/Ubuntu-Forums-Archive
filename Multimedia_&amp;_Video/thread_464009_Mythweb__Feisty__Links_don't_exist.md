---
title: "Mythweb / Feisty : Links don't exist"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by neko on 2007-06-04
Hi,

I've been using Mythweb installed on breezy for 18 months.  Worked perfectly.

I've just upgraded to Feisty and for a number of reasons did a complete reinstall, including Mythtv (installed via apt-get).

I've just about got everything up and running again.... except MythWeb.  I can't believe the install package was this badly broken, so I must have done something very wrong.....

[LIST=1]
[*]Loading [http://myserver/mythweb](http://myserver/mythweb) just brings up the directory listing, rather than opening mythweb.php.   I can easily add a symlink from index.php to mythweb.php, but I shouldn't have to.  Have I missed enabling something in apache2 that will automatically load mythweb.php ?

[*]None of the links on the main MythWeb page work for me.  For instance, the "TV" link points to [http://myserver/mythweb/tv](http://myserver/mythweb/tv).  Similarly, the "video" link points to [http://myserver/mythweb/video](http://myserver/mythweb/video).  None of these directories were installed when I installed the mythweb package.  There is relevant stuff existing under /my/root/mythweb/modules/tv and modules/video .  Like I said, I can't believe that the installer is so broken that it creates this links that don't point to anything.  Do I need to correct the links in the PHP?  Create symlinks to each to TV, Video, Weather, etc?
[/LIST]

Thanks for any help/advice.

---

### Post by Scorpuk on 2007-06-04
It certainly sounds like something is missing.

When I upgraded to 7.04, bout 2 weeks after issue, I reinstalled mythtv from scratch too, but mine worked straight away.


Maybe if you removed the mythweb package and tried reinstalling it.



Worth a shot before you have to do something more drastic...


Anywho hope ya get it working.

---

### Post by neko on 2007-06-04
Thanks for the suggestion -- but I'd already removed/reinstalled the mythweb package about 5 times.

The good news is that I think I've now fixed the problem.

This entry in apache2/httpd.conf was permitting me to view the main mythweb page from [http://myserver/mythweb:](http://myserver/mythweb:)

```
    <Directory "/usr/share/mythtv/mythweb">
      Options Indexes FollowSymLinks
      AuthType Digest
      AuthUserFile /var/www/mythweb/.htaccess
      AllowOverride All
    </Directory>
```

Apparently .htaccess was being read, because the db_* variables were being assigned.  But it wasn't until I added the line:
```
Alias /mythweb "/usr/share/mythtv/mythweb"
```
to httpd.conf that the user authentication specified in .htaccess started to be used, and it wasn't until I uncommented the line:
 ```
   RewriteBase    /mythweb
```
in .htaccess that the links on the main mythweb page started to magically work.

---

