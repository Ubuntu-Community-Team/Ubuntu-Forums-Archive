---
title: "Cannot get .htaccess to work in /var/www/"
date: 2009-02-19
forum: Mythbuntu
---

### Post by covert on 2009-02-19
My .htaccess file works fine for mythtv (/usr/share/mythtv/mythweb/.htaccess) but will not work for /var/www/.htaccess

I have even copied the file from /mythweb to /www just to make sure it was not a file issue.

As far as I can tell it is a setup issue with apache.

I have also tried to add this to /etc/apache2/apache2.conf
```
<Directory /var/www/>
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     allow from all
     # Uncomment this directive is you want to see apache2's
     # default start page (in /apache2-default) when you go to /
     #RedirectMatch ^/$ /apache2-default/
</Directory>
```

I have also tried putting a .htaccess file into /var/www/test and navigating to [http://mythip/test/](http://mythip/test/) and .htaccess still fails.

So the only .htaccess file being respected by apache is the one in the mythweb directory.

System is Mythbuntu 8.04

I have not found any errors in the apache error log either.

Any help to get .htaccess working in other directories besides mythweb would be great appreciated.

---

### Post by volkswagner on 2009-02-19
You may want to explain what you are trying to accomplish, and include some details of the file.  There are many things that an .htaccess can perform.  Some functions may require an .htpasswd file also.

---

### Post by covert on 2009-02-19
I am trying to make a password required to view any part of the web server.

Current .htaccess file is

```

AuthUserFile /var/.htpasswd_mythweb
AuthGroupFile /dev/null
AuthName MythWeb
AuthType Basic

require user mythtv
Options +Indexes

```

This file works fine in mythweb folder but does not work int /var/www/ or /var/www/test/

---

### Post by volkswagner on 2009-02-19
I just performed the following how to.  It worked a treat.  This has been on my "to-do" list.

[http://www.cs.dal.ca/studentservices/faq/tutorials/web_sites/htaccess.shtml](http://www.cs.dal.ca/studentservices/faq/tutorials/web_sites/htaccess.shtml)

---

### Post by covert on 2009-02-19
Thanks for the How-To but still does not work for me. Something in Mythbuntu Apache setup seems to be ignoring the .htaccess file and I jsut can't seem to find what it is.

---

### Post by OKKARE on 2009-03-04
I have a similar problem. All .htaccess files seem to be ingnored on Ubuntu. I installed using bitnami. And it was the same when I installed manually. I;ve edited the httpd.conf to allow this, but still now joy. I think Ubuntu blocks .htaccess from working.

I can't even do redirects. And some of my other software requires it's .htaccess to work.

---

### Post by covert on 2009-03-10
Found the solution.

Edit /etc/apache2/sites-available/default

Make the following change in bold.
```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride **All**
                Order allow,deny
                allow from all
        </Directory>

```

---

