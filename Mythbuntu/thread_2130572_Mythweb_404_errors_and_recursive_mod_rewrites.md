---
title: "Mythweb 404 errors and recursive mod_rewrites?"
date: 2013-03-29
forum: Mythbuntu
---

### Post by Fynn on 2013-03-29
***Post updated for clarification.***

My mythtv server (named "myth") runs apache with a few different vhosts.  One of them I set up for mythweb.  I've tried a few different ways of setting up the apache config, but each time it seems to fail to access the sub-pages in mythweb.

If I browse to [http://myth/](http://myth/) what my browser actually shows is the same as [http://myth/mythweb.php](http://myth/mythweb.php).

But if I click on any of the sub-pages, for example **[http://myth/tv/list](http://myth/tv/list)** I get a 404 error:

```
The requested URL /mythweb.php/tv/list was not found on this server.
```

This is the same error as if I'd browsed directly to **[http://myth/mythweb.php/tv/list](http://myth/mythweb.php/tv/list)**.

So, is my mod_rewrite doing what it should be?  Is the problem elsewhere?

I've consolidated everything into one apache conf file for simplicity:

```

NameVirtualHost *

<Proxy *>
Allow from 127.0.0.1
</Proxy>

<VirtualHost *>
        ServerName myth
        ServerAlias myth
        DocumentRoot "/var/www/mythweb/"
        Options indexes followsymlinks
    <Directory "/var/www/mythweb/data">
        Options -All +FollowSymLinks +IncludesNoExec
    </Directory>
    <Directory "/var/www/mythweb">
        AuthType           Digest
        AuthName           "MythTV"
        AuthUserFile       /etc/mythtv/mythweb-digest
        Require            valid-user
        BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
        Order              allow,deny
        Satisfy            any
        <Files mythweb.*>
            setenv db_server        "localhost"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "abcdefg12"
        </Files>
        <Files *.php>
                php_value safe_mode                     0
                php_value register_globals              0
                php_value magic_quotes_gpc              0
                php_value file_uploads                  0
                php_value allow_url_fopen               On
                php_value zlib.output_handler           Off
                php_value output_handler                NULL
                php_value memory_limit                  64M
                php_value max_execution_time            30
                php_flag output_handler                 "NULL"
        </Files>
        RewriteEngine on
        RewriteRule ^(css|data|images|js|themes|skins|README|INSTALL|[a-z_]+\.(php|pl))(/|$)     -     [L]
        RewriteRule ^(pl(/.*)?)$            mythweb.pl/$1               [QSA,L]
        RewriteRule ^(.+)$                  mythweb.php/$1              [QSA,L]
        RewriteRule ^(.*)$                  mythweb.php                 [QSA,L]
        AllowOverride all
        Options FollowSymLinks
        AddType video/nuppelvideo   .nuv
        AddType image/x-icon        .ico
        BrowserMatch ^Mozilla/4 gzip-only-text/html
        BrowserMatch ^Mozilla/4\.0[678] no-gzip
        BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
        AddOutputFilterByType DEFLATE text/html
        AddOutputFilterByType DEFLATE text/css
        AddOutputFilterByType DEFLATE application/x-javascript
        <Files *.pl>
            SetHandler cgi-script
            Options +ExecCGI
        </Files>
    </Directory>
</VirtualHost>
...

#other vhosts go here

```

---

### Post by Fynn on 2013-04-06
Ah!  Solved it!

Don't know why, but url variables were not being recognised if they were separated from the filename by a forward slash.  It seemed to treat the whole string as a filename, and then decided that it did not exist.  I replaced the commented out lines with the two using ?PATH_INFO= and things seem happy.

```

#       RewriteRule ^(pl(/.*)?)$            mythweb.pl/$1               [QSA,L]
#       RewriteRule ^(.+)$                  mythweb.php/$1              [QSA,L]
        RewriteRule     ^(pl(/.*)?)$           mythweb.pl?PATH_INFO=/$1    [L,QSA]
        RewriteRule     ^(.+)$                 mythweb.php?PATH_INFO=/$1   [L,QSA]

```

---

