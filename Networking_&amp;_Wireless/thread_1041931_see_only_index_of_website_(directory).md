---
title: "see only index of website (directory)"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by borobudur on 2009-01-17
Hi, I removed *phpldapadmin* by accident. Then I installed it again. Now if I brows to its address I just see the websites index, the content of that directory :-(
```
Index of /
[ICO]    Name    Last modified    Size    Description
[ ]    apache.conf    16-Jan-2009 22:57     1.1K
[ ]    config.php    17-Jan-2009 09:45     23K
[ ]    config.php.backup    09-Sep-2008 15:50     23K
[DIR]    templates/    29-Dec-2008 10:17     -
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch proxy_html/3.0.0 Server at ldap.domain.org Port 80
```The **config.php** has still the necessary values and in the **apache.conf** points to the phpldapadmin directory:
```
# Define /phpldapadmin alias, this is the default
<IfModule mod_alias.c>
    Alias /phpldapadmin /usr/share/phpldapadmin/htdocs
</IfModule>

# You can also use phpLDAPadmin as a VirtualHost
#<VirtualHost *:*>
#     ServerName phpldapadmin.domain.org
#     ServerAdmin root@example.com
#     DocumentRoot /usr/share/phpldapadmin
#     ErrorLog logs/ldap.example.com-error.log
#     CustomLog logs/ldap.example.com-access.log common
#</VirtualHost>

<Directory /usr/share/phpldapadmin/htdocs/>

    DirectoryIndex index.php
    Options +FollowSymLinks
    AllowOverride None

    Order allow,deny
    Allow from all

    <IfModule mod_mime.c>

      <IfModule mod_php4.c>
        AddType application/x-httpd-php .php

        php_flag magic_quotes_gpc Off
        php_flag track_vars On
        php_flag register_globals On
        php_value include_path .
      </IfModule>

      <IfModule !mod_php4.c>
        <IfModule mod_actions.c>
          <IfModule mod_cgi.c>
            AddType application/x-httpd-php .php

            Action application/x-httpd-php /cgi-bin/php4
          </IfModule>
        </IfModule>
      </IfModule>

    </IfModule>

</Directory>
```Can someone tell me what's the problem here?

Edited: by the way, an other important detail: I changed the access to the login by adding a virtual host (subdomain) *phpldapadmin.domain.org*. Perhaps this is the problem.

---

