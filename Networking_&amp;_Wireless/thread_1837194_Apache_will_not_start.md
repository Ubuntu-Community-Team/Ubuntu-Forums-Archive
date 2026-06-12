---
title: "Apache will not start"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by jhostettler on 2011-09-01
[FONT=Arial][SIZE=2]Hello, I am trying to set up apache as a reverse proxy. After trying to start the service using webmin i kept receiving errors. I fixed each error, and now when i try to start apache al i get is:[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Failed to start apache:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]* Starting web server apache2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Action 'start' failed.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]The Apache error log may have more information[/SIZE][/FONT]
[FONT=Arial][SIZE=2]...fail![/SIZE][/FONT]

[FONT=Arial][SIZE=2]I checked the error log and it had nothing pertaining to the error.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Her is my apache2.conf file.[/SIZE][/FONT]
 
LockFile ${APACHE_LOCK_DIR}/accept.lock
 
PidFile ${APACHE_PID_FILE}
 
Timeout 300
 
KeepAlive On
 
MaxKeepAliveRequests 100
 
KeepAliveTimeout 15
 
<IfModule mpm_prefork_module>
StartServers 5
MinSpareServers 5
MaxSpareServers 10
MaxClients 150
MaxRequestsPerChild 0
</IfModule>
 
<IfModule mpm_worker_module>
StartServers 2
MinSpareThreads 25
MaxSpareThreads 75 
ThreadLimit 64
ThreadsPerChild 25
MaxClients 150
MaxRequestsPerChild 0
</IfModule>
 
<IfModule mpm_event_module>
StartServers 2
MinSpareThreads 25
MaxSpareThreads 75 
ThreadLimit 64
ThreadsPerChild 25
MaxClients 150
MaxRequestsPerChild 0
</IfModule>
 
User ${APACHE_RUN_USER}
 
Group ${APACHE_RUN_GROUP}
 
AccessFileName .htaccess
 
<Files ~ "^\.ht">
Order allow,deny
Deny from all
Satisfy all
</Files>
 
DefaultType text/plain
 
HostnameLookups Off
 
ErrorLog ${APACHE_LOG_DIR}/error.log
 
LogLevel warn
 
Include mods-enabled/*.load
 
Include mods-enabled/*.conf
 
Include httpd.conf
 
Include ports.conf
 
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
 
Include conf.d/
 
Include sites-enabled/
 
Here is the site-enabled file for the virtual hosts.
 
<VirtualHost *:80>
ServerAdmin webmaster@localhost
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
 
<VirtualHost *:5500>
RewriteEngine On
RewriteOptions Inherit 
 
## Proxy rules for ShoreTel iPhone App
# NOTE the rewrite rules have a proxy redirect
RewriteRule ^/theme/(.+)$ /director2/theme/$1 [P]
RewriteRule ^/yui_2.7.0/(.+)$ /director2/yui_2.7.0/$1 [P]
RewriteRule ^/js/(.+)$ /director2/js/$1 [P]
ProxyPass /authenticate/ [http://172.19.10.15/](http://172.19.10.15/)
ProxyPassReverse /authenticate/ [http://172.19.10.15/](http://172.19.10.15/)
ProxyPass /cas/ [http://172.19.10.15:5447/](http://172.19.10.15:5447/)
ProxyPassReverse /cas/ [http://172.19.10.15:5447/](http://172.19.10.15:5447/)
ProxyPass /director2/ [http://172.19.10.151:5449/](http://172.19.10.151:5449/)
ProxyPassReverse /director2/ [http://172.19.10.15:5449/](http://172.19.10.15:5449/)
ProxyPass / [http://172.19.10.15/](http://172.19.10.15/)
ProxyPassReverse / [http://172.19.10.15/](http://172.19.10.15/)
SSLEngine on
SSLProxyEngine on
SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
SSLCertificateFile "/etc/apache2/ideacom-networks.com.crt"
BrowserMatch ".*MSIE.*" nokeepalive ssl-unclean-shutdown downgrade-1.0 force-response-1.0
</VirtualHost>

---

