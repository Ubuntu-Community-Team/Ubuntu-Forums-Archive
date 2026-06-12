---
title: "Mediatomb please help ETERNALLY GRATEFUL"
date: 2012-10-08
forum: Multimedia Software
---

### Post by UbNoob87 on 2012-10-08
guys not sure why this is happen before but i'm getting this error 

> root@LT:/# mediatomb 

MediaTomb UPnP Server version 0.12.1 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2010 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2012-10-08 17:35:59    INFO: Loading configuration from: /home/lt/.mediatomb/config.xml
2012-10-08 17:35:59    INFO: Checking configuration...
2012-10-08 17:35:59    INFO: Setting filesystem import charset to UTF-8
2012-10-08 17:35:59    INFO: Setting metadata import charset to UTF-8
2012-10-08 17:35:59    INFO: Setting playlist charset to UTF-8
2012-10-08 17:35:59 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check [http://www.youtube.com/t/terms](http://www.youtube.com/t/terms)
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2012-10-08 17:35:59    INFO: Configuration check succeeded.
2012-10-08 17:35:59   ERROR: could not load correct lastID (db not initialize


I delete the database i try to remove and uninstall it so far no go :(

---

### Post by markba on 2013-01-05
I had the same problem, here is the solution:
[http://socrateos.blogspot.nl/2011/01/reset-mediatomb-database.html](http://socrateos.blogspot.nl/2011/01/reset-mediatomb-database.html)

Basically, drop the database and it will created again when starting mediatomb, a shiny and fresh one!

---

