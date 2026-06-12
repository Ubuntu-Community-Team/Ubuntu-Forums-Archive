---
title: "[SOLVED] Mythweb not working - php_value problem?"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by s13_mills on 2007-12-28
Hi all,

   On a new install of mythtv and associated plugins, including mythweb, mythweb will not work. I have successfully installed mythweb before (it was really easy, just sudo apt-get install mythweb) and it ran no problem, but this time it will not work properly at all!
   Following a restart of the apache server and an attempt to access mythweb, error.log contains:
```

[Sat Dec 29 11:25:16 2007] [notice] Digest: generating secret for digest authentication ...
[Sat Dec 29 11:25:16 2007] [notice] Digest: done
[Sat Dec 29 11:25:16 2007] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Sat Dec 29 11:25:21 2007] [alert] [client 192.168.1.100] /var/www/mythweb/.htaccess: Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
[Sat Dec 29 11:26:15 2007] [alert] [client 192.168.1.100] /var/www/mythweb/.htaccess: Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
```

This is really getting me down, as I find mythweb really useful! Any help will be appreciated! Thanks in advance!

---

### Post by s13_mills on 2007-12-29
Solved it - in the end I just reinstalled the whole OS and re-installed mythTV and mythweb - this seemed very windows-esque but at least its working now!

---

### Post by dboon2 on 2008-04-02
Could have also tried

 /usr/sbin/a2enmod php5

to enable the php module in apache2

---

