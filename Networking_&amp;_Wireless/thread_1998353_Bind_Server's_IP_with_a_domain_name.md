---
title: "Bind Server's IP with a domain name"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by Varemenos on 2012-06-06
I own a domain name "name.gr" and i also got a ubuntu server (11.10). I'd like to point the nameservers of the domain name to the server. Can anyone help me set it up properly? I have no idea how to even begin.
Thanks in advance

---

### Post by poolet on 2012-06-06
check the following links and warning:: 
[http://www.thesitewizard.com/domain/point-domain-name-website.shtml](http://www.thesitewizard.com/domain/point-domain-name-website.shtml)

::**Be careful with**::

**1.** Registrars - Some companies have tricky stuff that lock your domain and you can't sell it  or transfer it into another provider.

**2.** You should read and contact with your provider first before you continue to build your Apache 2 (LAMP server) - be sure that you know exactly what your are doing, search for more information with wiki and ubuntu community..
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html)
[http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29](http://en.wikipedia.org/wiki/LAMP_%28software_bundle%29)
[B]
3. [/B]Do not start with the following turorials before you finished part 1 and 2 and you have understand what's happens.  Authentication is very important thing, especially for admin users.. !!!
[http://httpd.apache.org/docs/2.0/mod/mod_auth_ldap.html](http://httpd.apache.org/docs/2.0/mod/mod_auth_ldap.html)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html)
[http://www.debianhelp.co.uk/apachead.htm](http://www.debianhelp.co.uk/apachead.htm)

**4.** If your using database into your website you need to build and setup MySql (with php & phpmyadmin to have access into your website... *optional if can do that from terminal if you want... ) check the first link on part 1. and the following links(3 links you can pick one..)::
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)
[http://www.ubuntugeek.com/howto-install-mysql-database-server-with-phpmyadmin-frontend.html](http://www.ubuntugeek.com/howto-install-mysql-database-server-with-phpmyadmin-frontend.html)
[http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/)

**5.** Go back to part 3 and confirm that your LAMP server is working ping the ip address of the server and as well for the localhost, best job is to ping the server from other computer in the same network and capture the network with wireshark to check for delays or any problems that it would appear..... 
[http://blog.sudobits.com/2010/06/23/how-to-install-wireshark-on-ubuntu-10-04/](http://blog.sudobits.com/2010/06/23/how-to-install-wireshark-on-ubuntu-10-04/)
[http://wiki.wireshark.org/CaptureSetup](http://wiki.wireshark.org/CaptureSetup)

Good Luck!!!!!

---

### Post by Varemenos on 2012-06-07
Hey, thanks for the great reply.
I set my domain name's A Record to the static IP of my server and now everything works just fine (well, i also had to add a redirect rule on my .htaccess to redirect all 'www.' urls to the same ones without the 'www.').

---

