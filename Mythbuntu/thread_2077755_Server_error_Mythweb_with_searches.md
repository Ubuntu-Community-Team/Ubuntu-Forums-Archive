---
title: "Server error Mythweb with searches"
date: 2012-10-29
forum: Mythbuntu
---

### Post by androidoc on 2012-10-29
I am new to mythtv and was able to get it up and running after a lot of reading. 

When I run searches: [Movies, 3½ Stars or more], [Children's movies], [Music Specials], [Science Fiction Movies] I run into no problems.
 
However I get: Server error when using mythweb other searches:

New Titles, Premieres
Movies
Movies, Stinkers (2 Stars or less)
Non-Series HDTV
All HDTV
Non-Music Specials

The error is: 
> The website encountered an error while retrieving [http://192.168.1.9/mythweb/tv/search/canned%3ANew%20Titles%2C%20Premieres](http://192.168.1.9/mythweb/tv/search/canned%3ANew%20Titles%2C%20Premieres). It may be down for maintenance or configured incorrectly.

HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request

When I looked at the Apache Error log I get the following:

> [Mon Oct 29 09:02:20 2012] [error] [client 192.168.1.113] PHP Fatal error:  Allowed memory size of 67108864 bytes exhausted (tried to allocate 1024 bytes) in /usr/share/mythtv/bindings/php/MythBase.php on line 30, referer: [http://192.168.1.9/mythweb/tv/searches](http://192.168.1.9/mythweb/tv/searches)
[Mon Oct 29 09:02:20 2012] [error] [client 192.168.1.113] File does not exist: /var/www/favicon.ico


Any thoughts on how I can fix this error?
It seems like its related to memory issue. How can I adjust the memory properly?

I already tried changing the memory limit in php.ini to 256 from 128MB.

Any other suggestions?

---

### Post by ycats on 2013-01-02
Change the following line in */etc/apache2/sites-enabled/mythweb.conf* and restart apache.


**php_value memory_limit 64M**

to 

**php_value memory_limit 128M**

---

