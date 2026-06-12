---
title: "Having trouble setting up Apache2"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by imhotep531 on 2011-08-08
I'm not able to access my website hosted on my home server from outside my network using [www.mydomain.com]("http://www.mydomain.com").  I'll provide all info I can think of.  Thanks for your help.

I'm running Ubuntu Server 10.04.2 LTS with apache2 installed.  I have a registered domain with Dotster ([www.curtsplace.com]("http://www.curtsplace.com")) and have added all of the required DYNDNS name servers to the Dotster account.  DynDNS account is active and setup properly.  ddclient is installed and configured on my server.  I'm also forwarding port 22 for SSH, port 80 to 8080 and port 443 to 8081 on my router.

I'm able to connect to my server from outside my network using SSH.  I can type my domain name into putty and it will connect me to my server from elsewhere on the web with no problems.  So I know ddclient and dyndns are setup properly.

When I try to hit my domain in a browser I get Not Found, the requested URL was not found on this server.

Here's the contents of /etc/apache2/sites-available/default

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName curtsplace.com
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

```Here's the contents of /etc/apache2/ports.conf

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 8080

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 8081
</IfModule>

<IfModule mod_gnutls.c>
    Listen 8081
</IfModule>

```

Thanks for your help

---

### Post by lkjoel on 2011-08-08
Could you give me the output of this Terminal command?
```
ls -A /var/www

```

---

### Post by imhotep531 on 2011-08-08
Here you go:

```
root@datahaus:/etc/apache2# ls -A /var/www
index.html

```

---

### Post by lkjoel on 2011-08-08
Try this:
```
sudo a2ensite default

```

---

### Post by imhotep531 on 2011-08-08
```
root@datahaus:/etc# a2ensite default
Site default already enabled
```

FYI, when I try to restart apache2 I get the following:

```
root@datahaus:/etc# service apache2 restart
 * Restarting web server apache2                                                                                                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

---

### Post by imhotep531 on 2011-08-08
I just got it to work by editing /etc/apache2/ports.conf as follows

Top line used to read:

```

<VirtualHost *:80>
```

I changed it to read:

```

<VirtualHost *:8080>
```

Now I'm able to hit my site in a browser by typing in the URL.  I am outside the server's LAN right now by the way.  This is what I wanted, but is there any reason I should not use this fix?

---

### Post by lkjoel on 2011-08-08
The problem relies in:
> ...
apache2: Could not reliably determine the server's fully qualified domain name, [COLOR=Red]**using 127.0.1.1 for ServerName**[COLOR=Black]
That means that it can only be used locally (only by the server).
[/COLOR][/COLOR]

---

### Post by imhotep531 on 2011-08-08
Thanks but please read my previous reply.  I edited /etc/apache2/sites-available/default and now I can access it from anywhere.

I'm not sure if this is a good fix or not...?

---

### Post by lkjoel on 2011-08-08
No it isn't a good fix. Most browsers contact port 80, and not port 8080.

What's your website's name? I could check to see if your configuration works on my computer.

---

### Post by imhotep531 on 2011-08-08
FYI (in my original post) Port 80 is currently being forwarded to 8080 via my router.

It's fine, I'm able to access it now with a standard URL.  Thanks.

---

### Post by lkjoel on 2011-08-08
If it's being forwarded, then that's fine.

---

### Post by imhotep531 on 2011-08-08
Here's the URL if you want to check it:

[www.curtsplace.com](www.curtsplace.com)

Thanks for the help.

---

### Post by lkjoel on 2011-08-08
Glad to know it works!

---

### Post by imhotep531 on 2011-08-09
[FONT=Arial][SIZE=2]Yeah but its strange that none of the tutorials I found, nor my book on Ubuntu, explain that you need to edit the top line of ports.conf so that 80 is replaced with whatever port you are going to listen to.  All it said was to add the 'Listen' directives further down within ports.conf but I had to edit the very first tag to include the specific port.  It makes me wonder if 443 is even being heard on my server right now.  I wonder if I need to create a separate tage for...
[/SIZE][/FONT][FONT=Arial][SIZE=2]NameVirtualHost *:8081

...and then basically copy the contents of the first one but with specific Listen directives for 8081.
[/SIZE][/FONT]

---

