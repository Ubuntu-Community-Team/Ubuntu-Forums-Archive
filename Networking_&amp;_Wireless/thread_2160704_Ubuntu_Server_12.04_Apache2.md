---
title: "Ubuntu Server 12.04 Apache2"
date: 2013-07-07
forum: Networking &amp; Wireless
---

### Post by xbooow59 on 2013-07-07
So, this has been something ive had trouble with since i started networking a year ago, and i have yet to find the soulution to the issue.
so i want to run more than one site on my server, and ive had one site run fine. so today i decided i wanted to try again so i followed this to help me.[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412) however, it didnt help me too much.

```
root@spencer:/etc/apache2/sites-available# service apache2 restart * Restarting web server apache2                                                                                        [Sun Jul 07 21:38:31 2013] [error] (EAI 5)No address associated with hostname: Could not resolve host name http://wootagemaster.adultdns.net -- ignoring!
[Sun Jul 07 21:38:31 2013] [error] (EAI 5)No address associated with hostname: Could not resolve host name http://spencers-music.dnsd.me -- ignoring!
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Jul 07 21:38:31 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Jul 07 21:38:31 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sun Jul 07 21:38:32 2013] [error] (EAI 5)No address associated with hostname: Could not resolve host name http://wootagemaster.adultdns.net -- ignoring!
[Sun Jul 07 21:38:32 2013] [error] (EAI 5)No address associated with hostname: Could not resolve host name http://spencers-music.dnsd.me -- ignoring!
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Jul 07 21:38:32 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Jul 07 21:38:32 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                 [ OK ]
root@spencer:/etc/apache2/sites-available# 



```
thats what i get on a restart.

the two sites in question are 
[http://wootagemaster.adultdns.net/](http://wootagemaster.adultdns.net/)
[http://spencers-music.dnsd.me/](http://spencers-music.dnsd.me/)
as you can tell by clicking, whatever i did didnt change anything.
```
<VirtualHost http://spencers-music.dnsd.me:80>        ServerAdmin spencer@localhost
        ServerName  http://spencers-music.dnsd.me
        ServerAlias spencers-music.dnsd.me


        DocumentRoot /var/www/
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
</VirtualHost>



```

```

<VirtualHost http://wootagemaster.adultdns.net:80>
        ServerAdmin dario@localhost
        ServerName  http://wootagemaster.adultdns.net
        ServerAlias wootagemaster.adultdns.net
        DocumentRoot /home/dario
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/dario>
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
</VirtualHost>





```
theres the two sites code, im not sure the issue and i have no idea how to fix it, thank you for rading this and taking time to answer if you do.

---

### Post by newbie-user on 2013-07-09
Change your virtual host declarations to:
```
<VirtualHost *:80>
```
The ServerName line will take care of the named-based virtual hosting. That should take care of this error:
```
[Sun Jul 07 21:38:32 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Jul 07 21:38:32 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
```
Then you can edit your /etc/hosts file to add your FQDN:
```
127.0.1.1  spencers-music.dnsd.me
```
and that should take care of this error:
```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by xbooow59 on 2013-07-10
thank you so much, this has been bugging me for like forever. im actually 17 and i think i might be a linux IT after college, its something im actually good at. granted i finally had to ask for help, but thats what linux is all about. cheers!

---

