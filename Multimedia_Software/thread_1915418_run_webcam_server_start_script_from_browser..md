---
title: "run webcam server start script from browser."
date: 2012-01-26
forum: Multimedia Software
---

### Post by JointTech on 2012-01-26
I have a php script which contains:
[PHP]shell_exec("/etc/init.d/webcam-server start");
sleep(3);
shell_exec("streamer -o /var/www/images/topshots/{$today}.jpeg");
sleep(3);
shell_exec("/etc/init.d/webcam-server start");[/PHP]

This works correctly if I run from a command line
php /var/www/takepicture.php

However if I run it from a browser either [http://localhost/takepicture.php](http://localhost/takepicture.php) or from another pc at [http://ipaddress/takepicture.php](http://ipaddress/takepicture.php) it does not work.

This part of the code Does work from a browser.
 [PHP]shell_exec("streamer -o /var/www/images/potshots/{$today}.jpeg");
[/PHP]

Its only the start and stop scripts that dont seem to have the proper permissions or something.
running Ubuntu 10 LTS Desktop version

---

### Post by JointTech on 2012-01-26
I was able to get it to work by changing apache to run as my local user account.  This is a closed system and security is not a concern.

---

