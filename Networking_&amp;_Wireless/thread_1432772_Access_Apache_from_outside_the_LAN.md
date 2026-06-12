---
title: "Access Apache from outside the LAN"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by raffaele181188 on 2010-03-18
I have set up a hostname on dyndns.com and configured my router to forward port 8181, but I cannot view it from the internet (FF says "can't establish a connection to the server"). The DNS is ok, is just the apache webserver that doesn't work.
I can acces my webserver from
[http://localhost:8181](http://localhost:8181)    (loopback)
[http://192.168.1.1:8181](http://192.168.1.1:8181)   (in the LAN)
**BUT NOT <hostname>.dyndns.com**
Here is my site configuration
```

<VirtualHost *:8181>
	ServerAdmin webmaster@localhost
	ServerName <hostname>.dyndns.com

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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```
And, of course, my ports.conf
```

NameVirtualHost *:8181
Listen 8181

```
So, what's the matter? How can I reach my apache from the internet? Also, I read about routers loopback errors, but this seems not related to it, since I tried to get it through a proxy server, and it failed

---

### Post by raffaele181188 on 2010-03-18
It seems kinda port forwarding problem.. I can get it with SOME proxy service :/

---

