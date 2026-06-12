---
title: "MythWeb is an hour in the future"
date: 2007-11-22
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-22
I just discovered that the time shown at the top of the Mythweb page is one hour in the future.  This also causes all it's program listings to be shown starting an hour late.


The mythbuntu box is set to the correct time.


Anyone know how can I fix this?

---

### Post by ubnewbie2 on 2007-11-23
I think I fixed it,  I found this post
[http://www.gossamer-threads.com/lists/mythtv/users/229018?search_string=mythweb%20time;#229018](http://www.gossamer-threads.com/lists/mythtv/users/229018?search_string=mythweb%20time;#229018)

tthat suggests defining the date.timezone value in the php.ini file (which I had trouble finding - it's in /etc/php5/apache2)

Well I did that, and now mythweb is running on the right time !

I hope it stays fixed.:(

---

### Post by oblong on 2008-01-01
> **ubnewbie2 said:**
> I think I fixed it,  I found this post
[http://www.gossamer-threads.com/lists/mythtv/users/229018?search_string=mythweb%20time;#229018](http://www.gossamer-threads.com/lists/mythtv/users/229018?search_string=mythweb%20time;#229018)

tthat suggests defining the date.timezone value in the php.ini file (which I had trouble finding - it's in /etc/php5/apache2)

Well I did that, and now mythweb is running on the right time !

I hope it stays fixed.:(
Thanks for that. Timezones are listed here: [http://us3.php.net/manual/en/timezones.php](http://us3.php.net/manual/en/timezones.php)
Quotes are not needed. Apache needs to be restarted:
sudo /etc/init.d/apache2 restart

Now we'll have to wait until the end of daylight saving to see if it still works!

---

