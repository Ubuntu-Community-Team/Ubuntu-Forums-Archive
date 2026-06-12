---
title: "can't enable mod_rewrite on local apache server?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2011-08-18
I have a base install of a LAMP server on my system, and I'm trying to get mod_rewrite working on that local server (the directory of the local site is [http://localhost/project](http://localhost/project)). I added this to my /etc/apache2/httpd.conf file, which was blank before I did so:

```

<Directory />
Options FollowSymLinks
AllowOverride All
Order deny,allow
Deny from all
Satisfy all
</Directory>

```

and I ran this command to enable mod_rewrite:
```

sudo a2enmod rewrite

```

I have this code in [http://localhost/project/.htaccess](http://localhost/project/.htaccess), which works on another site on a shared server elsewhere:
```

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond $1 !^(index\.php|ajax|css|error|img|js)
RewriteRule ^(.*)$ index.php?url=$1 [PT,L]
</IfModule>

```

It's supposed to redirect everything except the listed directories to index.php, which is used as a front controller. However, if I type in http://localhost/project/<any other page> I get a 404 error. 

Any ideas?
Thank you!

---

### Post by georgemc on 2011-08-18
Is the psychical location of those files some where in “/var/www”? 

Which is the default “DocumentRoot” for Apache2.  It might be a configuration issue because usually URL paths and not the same as File System paths.

 For example for:
 
 http://localhost/project/<any other page>
 
 Apache2 will look for it in: /var/www/localhost/project/<any other page>
 
 Unless you configure “DocumentRoot” in the “/etc/apache2/sites-available/default” to point to a different location.
 

 Hope this helps.
 

 George

---

### Post by pythonscript on 2011-08-18
I'm not entirely sure how to check what the DocumentRoot is set to, but I haven't changed it, and the files are in /var/www/project/. If I browse to [http://localhost/project/](http://localhost/project/) or [http://localhost/index.php](http://localhost/index.php), I reach the right page. Otherwise, though, I don't.

---

### Post by georgemc on 2011-08-18
Ok – need to correct myself.
 
 Apache2 default will look for  

 http://localhost/project/<any other page>
 in: /var/www/project/<any other page>
 
 So: [http://localhost/project/index.php](http://localhost/project/index.php)
 
 points to > /var/www/project/index.php
 
 So far looks like it should. Now I am using sub-directories in /var/www and they do work, just need to watch out for spelling and case.  Remember in *NIX file names are case sensitive.  I would also avoid files names with spaces, tabs, any kind of quotes etc.

 The apache2 configuration files are located in “/etc/apache2”.  Specifically look into “/etc/apache2/site-available/default” and the entries for “DocumentRoot” should be  “/var/www” and check the <Directory> directives.  Those control what can be seen.  The default version should just work.
 
 Other Apache2 config files are “httpd.conf” and “ports.conf” they should just work from default.  It you have any “.htaccess” files I would rename them (I had some issues early on) to “DOThtaccess” so they wont be used and don’t interfere with trouble shooting.
 
 For example I have a directory in “/var/www” named “MyProject” and in there a a file name “FeedBack_Form.php”.  To invoke it from a browser its “[http://localhost/MyProject/FeedBack_Form.php”]("http://localhost/MyProject/FeedBack_Form.php%E2%80%9D")
 
 Good reference links that I use are:
 
 [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
 [http://www.php.net/manual/en/manual.php](http://www.php.net/manual/en/manual.php)
 [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)
 

 George

---

### Post by pythonscript on 2011-08-19
My default file has this as its DocumentRoot entries that pertains to /var/www:
```

DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

```

Is AllowOverride None causing the problem here? None of my directories in /var/www has any problematic characters in their filesnames (spaces, tabs, quotes), either.

---

### Post by pythonscript on 2011-08-19
I changed AllowOverride None to AllowOverride All, and it's working. Thank you for the help!

---

