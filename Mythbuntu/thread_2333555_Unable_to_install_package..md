---
title: "Unable to install package."
date: 2016-08-11
forum: Mythbuntu
---

### Post by moni-kumbhakar on 2016-08-11
ubuntu 16.04 unable to install any package, I google it and try  every thing but its not help.

It's showing like:

```

After this operation, 0 B of additional disk space will be used.
Setting up php5.6-fpm (5.6.24-1+deb.sury.org~xenial+1) ...
Error: The new file /usr/lib/php/5.6/php.ini-production does not exist!
dpkg: error processing package php5.6-fpm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5.6:
 php5.6 depends on libapache2-mod-php5.6 | php5.6-fpm | php5.6-cgi; however:
  Package libapache2-mod-php5.6 is not installed.
  Package php5.6-fpm is not configured yet.
  Package php5.6-cgi is not installed.

dpkg: error processing package php5.6 (--configure):
 dependency problems - leaving unconfigured
Setting up php7.0-fpm (7.0.9-1+deb.sury.org~xenial+1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Not replacing deleted config file /etc/php/7.0/fpm/php.ini
NOTICE: Not enabling PHP 7.0 FPM by default.
NOTICE: To enable PHP 7.0 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.0-fpm
NOTICE: You are seeing this message because you have apache2 package installed.
Job for php7.0-fpm.service failed because the control process exited with error code. See "systemctl status php7.0-fpm.service" and "journalctl -xe" for details.
invoke-rc.d: initscript php7.0-fpm, action "restart" failed.
dpkg: error processing package php7.0-fpm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 php5.6-fpm
 php5.6
 php7.0-fpm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

