---
title: "Can't access my apache webserver from the internet"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by catsrules on 2012-01-24
I can't access my web sight I am hosting from home, over the internet. I have port forwarded port 80 to my web server at 172.16.10.12. 
But when I try to access the server from a computer off my local network (My cell phone over 3G) using my public ip 24.10.151.XXX, it doesn't show up. I can use my public ip and access the server from a local computer.
I know it has something to do with ubuntu or apache, because I can change my port forwarding settings to my network printer's IP and access it's setup page from my public IP and with my cell phone using 3G.

my Apache default file

<VirtualHost 172.16.10.12:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www/owncloud
    ServerName owncloud
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/owncloud>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

