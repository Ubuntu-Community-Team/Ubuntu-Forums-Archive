---
title: "Troubleshoot Mythweb?"
date: 2013-01-17
forum: Mythbuntu
---

### Post by dannyboy79 on 2013-01-17
I didn't do anything to my system except maybe some apt-get updates and upgrades and now my Mythweb doesn't work. 

I am not sure where to begin to troubleshoot this. Here's come of apache2 access.log and error.log if that helps?
access.log
```
173.89.62.76 - daniel [17/Jan/2013:01:41:14 -0600] "GET /mythweb/status HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
173.89.62.76 - - [17/Jan/2013:01:41:14 -0600] "GET /favicon.ico HTTP/1.1" 404 509 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:42:52 -0600] "GET / HTTP/1.1" 200 390 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:42:52 -0600] "GET /favicon.ico HTTP/1.1" 404 503 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:42:55 -0600] "GET /mythweb HTTP/1.1" 401 749 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - daniel [17/Jan/2013:01:42:55 -0600] "GET /mythweb HTTP/1.1" 301 558 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - daniel [17/Jan/2013:01:42:55 -0600] "GET /mythweb/ HTTP/1.1" 500 275 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:46:13 -0600] "GET /index HTTP/1.1" 200 457 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:46:13 -0600] "GET /favicon.ico HTTP/1.1" 404 503 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11"
192.168.0.3 - - [17/Jan/2013:01:46:27 -0600] "-" 408 0 "-" "-"
```

error.log
```
[Thu Jan 17 01:40:31 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Thu Jan 17 01:41:05 2013] [error] [client 173.89.62.76] PHP Warning:  require(modules/_shared/tmpl/tmpl/header.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:05 2013] [error] [client 173.89.62.76] PHP Fatal error:  require(): Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:12 2013] [error] [client 173.89.62.76] PHP Warning:  require(modules/_shared/tmpl/tmpl/header.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:12 2013] [error] [client 173.89.62.76] PHP Fatal error:  require(): Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:12 2013] [error] [client 173.89.62.76] File does not exist: /var/www/favicon.ico
[Thu Jan 17 01:41:14 2013] [error] [client 173.89.62.76] PHP Warning:  require(modules/_shared/tmpl/tmpl/header.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:14 2013] [error] [client 173.89.62.76] PHP Fatal error:  require(): Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:41:14 2013] [error] [client 173.89.62.76] File does not exist: /var/www/favicon.ico
[Thu Jan 17 01:42:52 2013] [error] [client 192.168.0.3] File does not exist: /var/www/favicon.ico
[Thu Jan 17 01:42:55 2013] [error] [client 192.168.0.3] PHP Warning:  require(modules/_shared/tmpl/tmpl/header.php): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:42:55 2013] [error] [client 192.168.0.3] PHP Fatal error:  require(): Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
[Thu Jan 17 01:46:13 2013] [error] [client 192.168.0.3] File does not exist: /var/www/favicon.ico

```

---

### Post by dannyboy79 on 2013-01-17
does anyone know where to start to troubleshoot this? basically nothing shows when I go to 192.168.0.5/mythweb even though it used to work just fine. there's a symlink within /var/www/mythweb which points to the location of the mythweb files. I don't know what to fix to get it working again, anyon help please

---

### Post by dannyboy79 on 2013-01-17
ok, so first I went into the file fatal.php and commented out line 23
```
sudo nano /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php
```
save the file, then tried mythweb and I got this:
[IMG]https://lh6.googleusercontent.com/-6O5t3fl6OwU/UPij-28mZ2I/AAAAAAAABZ8/fBcYLzbEkGI/s720/Screenshot%2520-%252001172013%2520-%252007%253A22%253A57%2520PM.png[/IMG]

So I when into my mythconverg database and dropped mythweb_sessions and everything started working. I even went back into fatal.php and uncommented line 23 and everything still is working.

YIPPIE!!

---

