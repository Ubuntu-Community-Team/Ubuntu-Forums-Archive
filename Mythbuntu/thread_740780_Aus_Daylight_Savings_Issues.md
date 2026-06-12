---
title: "Aus Daylight Savings Issues"
date: 2008-03-31
forum: Mythbuntu
---

### Post by nasha on 2008-03-31
Hey guys,
Having some issues with daylight savings... Ubuntu displays the correct time, mythfrontend displays the correct time on its theme background, but mythweb has the time an hour back...

Probably something stupid, but how do i fix this?

---

### Post by jbman on 2008-03-31
you need to update the php database, quick google and you will find what to do.

---

### Post by nasha on 2008-03-31
Not finding much relevant info on Google at the moment... Care to provide some more info?

---

### Post by jbman on 2008-03-31
check this out
[http://pecl.php.net/package/timezonedb](http://pecl.php.net/package/timezonedb)

and this
[http://ubuntuforums.org/showthread.php?t=620033](http://ubuntuforums.org/showthread.php?t=620033)

---

### Post by nasha on 2008-03-31
Unfortunately the ubuntu forums post didn't solve my problem :(
It appears to think the time is correct for my zone, but daylight savings isnt until this weekend..

EDIT:
Ok, complete hack job, but its a temporary fix until daylight savings actually starts here... I changed my timezone in the php.ini file to Asia/Vladivistok (The only other place in the world that has the same time as East Aus)

---

### Post by sfp on 2008-03-31
sudo apt-get install php5-dev

sudo pecl install timezonedb

Add the line to php.ini
extension=timezonedb.so

sudo /etc/init.d/apache2 restart

---

