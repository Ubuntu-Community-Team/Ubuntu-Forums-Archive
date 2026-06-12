---
title: "Wordpress install using Lamp"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by ipsofacto on 2012-04-26
Hello

I'm afraid this is going to be a long one: hold on to your hats...

I'm trying to set up a website running my own server using WP.  I have installed LAMP and everything locally seems to work fine locally , e.g. if i type ```
http://localhost/wordpress/
``` into my browser everything appears as it should i.e. my potential site.

However, whenever I try to go 'live' it all tends to go t!ts up.  The configuration I need help with is apache (far, far too complex!).

You should note that WP has been installed in /var/www/wordpress.  

```
$ ls /var/www
index.html  info.php  wordpress

```

WP Database has been created successfully using mySQL and PHPMYADMIN seems fine.  Basically everything works, I just need help to get to the next level and go 'public'.  I have set dns setting with the company that registered the domain name and have allowed port forwarding for port 80 on router.

Here are the files (I think) I need help with to tell apache where my domain will go (and possibly help with adding sym links in the process):

```
ipsofacto@MyBoX /etc/apache2/sites-enabled $ cat 000-default 
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

```

Any help/further questions much appreciated!  You should note that I am a nube and that I am trying to do this for having 'fun' with linux and learning as opposed for setting up a commercial site.  I will most prob move it to a company once up - just wanted th have a go myself !

---

### Post by loonabip on 2012-04-26
Ubuntu is a popular Linux based operating system. Linux is also a  popular platform for Web hosting. In order to host websites and other  Web applications on Ubuntu, you need to install software, such as LAMP  (Linux-Apache-MySQL-PHP) onto your system. Whether you plan to use this  Ubuntu installed computer for development and testing, or for production  hosting, the installation is the same.                            [LEFT][COLOR=#000000]



[B][local arts]("http://NorthernGroove.com")
[local music]("http://NorthernGroove.com")
[fort saint john]("http://NorthernGroove.com")
[fsj events]("http://NorthernGroove.com")[/B]

[/COLOR][/LEFT]

---

