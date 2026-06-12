---
title: "Apache stoped parsing php?"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by whitehaint on 2010-09-30
Just trying to narrow down a possible source, but my LAMP install (via synaptic) on 10.10 beta 64bit is not working fully!  HTML comes along fine, but php prompts to save or open instead of being parsed.  Phpmyadmin is not working either, just a pretty white page.  Removed and reinstalled and want to know if it's just me or if it's a bug.:popcorn:
The error log for Apache has this to say;

[Thu Sep 30 18:22:11 2010] [error] [client 127.0.0.1] PHP Fatal error:  php-gtk: Could not open display in Unknown on line 0

---

### Post by cariboo on 2010-09-30
Have you got libapache2-mod-php5 installed? It's in the repositories.

---

### Post by whitehaint on 2010-09-30
> **cariboo907 said:**
> Have you got libapache2-mod-php5 installed? It's in the repositories.

Yup! Reinstalled, restarted Apache and still not parsing.  I did however just do a search for php-gtk and came up with nothing, and that is searching all areas.

---

### Post by cariboo on 2010-09-30
Is mod-php5 enabled? It's in /etc/apache2/mods-enabled. I just trying to make sure all the i's are dotted and the t's crossed.

---

### Post by whitehaint on 2010-09-30
Yup, here are the contents:
```

<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
    SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
    SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
           php_admin_value engine Off
       </Directory>
    </IfModule>
</IfModule>
```

Interestingly I can run php from the CLI.  I ran a phpinfo and got this on the php-gtk:

php-gtk

GTK+ support => enabled
GTK+ v => 2.22.0

Directive => Local Value => Master Value
php-gtk.codepage => iso-8859-1 => iso-8859-1
php-gtk.extensions => no value => no value

---

### Post by whitehaint on 2010-10-01
*grumble grumble* Thought I had it but didn't! So far looks like a wipe and fresh install of 10.04 will be needed as that worked on another box.

---

### Post by liorwohl on 2010-10-02
i have this problem (download php file) when i go to [http://myserv/~username](http://myserv/~username)

but [http://myserv/](http://myserv/) (var/www) works good.

also change the config to display errors:
error_reporting = E_ALL & ~E_NOTICE
display_errors = On

---

### Post by whitehaint on 2010-10-02
> **liorwohl said:**
> i have this problem (download php file) when i go to [http://myserv/~username]("http://myserv/%7Eusername")

but [http://myserv/](http://myserv/) (var/www) works good.

also change the config to display errors:
error_reporting = E_ALL & ~E_NOTICE
display_errors = On


I did, however apache wasn't even attempting to parse php so there could be no error.  The apache log error was the same one about php-gtk on line 0.  I ended up backing up my data then nuking the install, rolled back to 10.04, installed lamp and all is working now.

---

