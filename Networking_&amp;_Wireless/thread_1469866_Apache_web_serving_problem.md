---
title: "Apache web serving problem"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-05-02
This is essentially my first Ubuntu experience, I was very good at windows machines though, and it's nice to use a more powerful command line... though it's very new to me.

Installed 10.4 on the release, an upgrade from 9.10 which I didn't use long enough to try Apache.

Using the instructions at
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
I installed Apache2 (and I think PHP and MYSql although I've not quite got around to configuring or using these)

I am trying to serve a regular webpage, nothing fancy just a hobby blog and it worked in windows apache just by setting the right directory (local) in the config file. Does anybody know how to get this to work?

I was getting a 403 error, now I just get ```
Index of /
Name	Last modified	Size	Description

Apache/2.2.14 (Ubuntu) Server at localhost Port 80
```

Here's my configuration file
```

<VirtualHost *:80>

	ServerAdmin [email]unacquainted@hotmail.co.uk[/email]

	DocumentRoot /home/samuel/Public/Web_server/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/samuel/Public/Web_server/>
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

EDIT: thought I might mention I'm on desktop edition, not server edition.

---

### Post by ironic.demise on 2010-05-02
Any help at all?
Using Opera's web server capabilities whilst in windows.
The Opera for Ubuntu seems to really struggle, although it "works" it doesn't serve the style.css correctly.
Wine-ing Opera is really just too slow, is that normal?

I don't own a DNS, so Apache jumped to my IP, which because I'm on mobile broadband, the IP kept changing (didn't trust giving my IP in windows anyway...)

- Is there a way to set static IP
- Is there a way to get Opera running web server efficiently
- Is there a way to make Wine run it faster
- Is there anything wrong with my Apache configuration? (well... obviously, but what is it?)

Solved!
~chmod -R 777 Web_server

---

