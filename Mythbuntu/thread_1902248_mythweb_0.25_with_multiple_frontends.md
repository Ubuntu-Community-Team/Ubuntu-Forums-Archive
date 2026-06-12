---
title: "mythweb 0.25 with multiple frontends"
date: 2011-12-30
forum: Mythbuntu
---

### Post by montge on 2011-12-30
If you're getting the following types of errors in youir apache2 error log AND you get nothing when you go to [http://media.local/mythtv](http://media.local/mythtv) (or whatever your hostname is AND you're running multiple frontends, you need to make some updates.

[Fri Dec 30 00:23:26 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.3 with Suhosin-Patch configured -- resuming normal  operations
[Fri Dec 30 00:23:31 2011] [error] [client 10.0.1.23] PHP Warning:  Failed to open translation file:  modules_path/_shared/lang/English.lang in /usr/share/mythtv/mythweb/classes/Translate.php on line 173
[Fri Dec 30 00:23:31 2011] [error] [client 10.0.1.23] File does not exist: /var/www/mythweb/skin_url, referer: [http://media.local/mythweb/](http://media.local/mythweb/)
[Fri Dec 30 00:23:31 2011] [error] [client 10.0.1.23] File does not exist: /var/www/mythweb/skin_url, referer: [http://media.local/mythweb/](http://media.local/mythweb/)
[Fri Dec 30 00:23:31 2011] [error] [client 10.0.1.23] File does not exist: /var/www/mythweb/skin_url, referer: [http://media.local/mythweb/](http://media.local/mythweb/)
[Fri Dec 30 00:23:31 2011] [error] [client 10.0.1.23] File does not exist: /var/www/mythweb/skin_urlimg, referer: [http://media.local/mythweb/](http://media.local/mythweb/)


[LIST]
[*]Needed to have correct paths in /etc/apache2/sites-available/mythtv.conf
[/LIST]
Instead of:
[FONT=courier new]    <Directory "/var/www/html/data">
        Options -All +FollowSymLinks +IncludesNoExec
    </Directory>
    <Directory "/var/www/html" >[/FONT]
Should be
[FONT=courier new]    <Directory "/var/www/mythweb/data">
        Options -All +FollowSymLinks +IncludesNoExec
    </Directory>
    <Directory "/var/www/mythweb" >[/FONT]

[LIST]
[*]Enable includes path in /etc/apache2/sites-available/mythtv.conf (note the mythtv/mythweb)
[/LIST]
[FONT=courier new]setenv include_path      "/usr/share/mythtv/mythweb/includes"[/FONT]



[LIST]
[*]Correct permissions for /usr/share/mythtv/mythweb/data/tv_icons for whatever reason mythweb wants write permissions to that directory.
[/LIST]
[FONT=courier new]sudo chgrp www-data /usr/share/mythtv/mythweb/data/tv_icons[/FONT]
 [FONT=courier new]sudo chmod g+w /usr/share/mythtv/mythweb/data/tv_icons[/FONT]

---

