---
title: "PHPMyAdmin Port Change"
date: 2009-11-17
forum: Mythbuntu
---

### Post by mitchell2345 on 2009-11-17
Hi,

I am running mythbuntu.

I have mythweb installed with a password and I just installed phpmyadmin.  Ubuntu installs this on port 80 along with mythweb.  I can view it by just adding phpmyadmin to the URL.

To increase security I would like to change the port number of phpmyadmin to 81.  This way I can still allow port 80 in from internet but have no chance of them hitting phpmyadmin.

My googles were saying to add a virtual host but things are not matching up.  I was following this:[http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/](http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/) 

mitchell@mythtv:/var/www-81$ cat /etc/apache2/sites-available/phpmyadmin
<VirtualHost 192.168.0.254:81>
  ServerName phpmyadmin
  DocumentRoot /var/www-81
</VirtualHost>

But cant telnet to port 81.  Does mythbuntu have the firewall enabled?  How do i move phpmyadmin into /var/www-81?  It doesnt have a folder in /var/www.

What am i missing?

Thanks,

-- 
Mitchell

---

### Post by mitchell2345 on 2009-11-17
Well tonight i spent some more time hacking away.

here is the steps:
remove symlink to phpmyadmin.conf file
```
rm /etc/apache2/conf.d/phpmyadmin.conf
```

make apache listen on port 81 (or what ever you desire.)
```
sudo nano /etc/apache2/ports.conf
```

Add "Listen 81" to the file.
```
user@mythtv:/etc/apache2$ cat ports.conf 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
Listen 81
<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

Now create the vHost:
```
sudo vi /etc/apache2/sites-available/phpmyadmin
```

add the following to the file:  
```
<VirtualHost *:81>
  ServerName phpmyadmin
  DocumentRoot /var/www-81
</VirtualHost>
```

Enable the vHost:
```
sudo a2ensite phpmyadmin
```

Restart Apache:
```
sudo service apache2 restart
```

Create a symlink to the phpmyadmin directoy:
```
cd /var/www-81
sudo ln -s /usr/share/phpmyadmin/
```

At this point navigating to [http://ip/phpmyadmin](http://ip/phpmyadmin) should not show the page.  but [http://ip:81/phpmyadmin](http://ip:81/phpmyadmin) should.

Now you can point you can nat your public IP to your MythTV box on port 80 allowing MythWeb but not allowing phpmyadmin since it lives on port 81.

---

### Post by jaffamuffin on 2010-07-17
Thanks man. This is exactly what I needed.  I'm running debian, and I had to do an extra restart of apache before it would work.

---

### Post by kiuz on 2010-11-20
perfect this work.
But after deleted 

rm /etc/apache2/conf.d/phpmyadmin.conf


PhpMyAdmin is visible in <local_Ip>/phpmyadmin/

I don't give acces at phpmyadmin by default path and port, want give acces only by <Local_ip>:81/phpmyadmin ....

---

### Post by pestolombardo on 2011-01-22
Hi,
I have experienced the same "problem": the web page was available on both ports 80 and 81.

I simply was loading a cached page, try to refresh the browser :D

Best

---

### Post by tester100 on 2011-11-11
Hi guys

came across the same problem today after installing ISPconfig webserver host ting..

phpmy admin stopped working which had been installed previously..

but instead i went to etc/phpmyadmin/phpmyadmin.service 

opened file and edited..

> <?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
 <name replace-wildcards="yes">phpMyAdmin on %h</name>
  <service>
   <type>_http._tcp</type>
   <port>80</port>
   <txt-record>path=/phpmyadmin/</txt-record>
  </service>
</service-group>


to another desired port

<port>xxxxx</port>

saved file

restarted apache and banged

localhost:81/phpmyadmin/

or local ip 192.xx.xx.xxx:81/phpmyadmin/

they both worked like a charm.

---

