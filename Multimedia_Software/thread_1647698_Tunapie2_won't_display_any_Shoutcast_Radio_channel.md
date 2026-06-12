---
title: "Tunapie2 won't display any Shoutcast Radio channels"
date: 2010-12-17
forum: Multimedia Software
---

### Post by vector_force on 2010-12-17
i am trying to list radio channels in Tunapie2 and it won't list anything.  It will display TV stations, but not radio.

I removed the software and Re-installed it with the same problem.  I even removed most files from my .tunapie folder under my home and just left prefs and favorites alone.  I did this before re-installing the software.

Icecast works fine, but not Shoutcast Radio.

Is this a server problem?



Rob

---

### Post by markthekdeguy on 2010-12-21
just tried tunapie here Rob, works ok.
maybe their server fell over :)

---

### Post by DapperMe17 on 2010-12-22
Shoutcast recently changed to 2.0 API...so there is probably a new streaming address. See...[http://www.shoutcastblog.com/2010/07/09/shoutcast-2-0-faq/](http://www.shoutcastblog.com/2010/07/09/shoutcast-2-0-faq/)

---

### Post by vector_force on 2010-12-23
Probably some API issues because Exaile isn't listing any Shoutcast radio stations either

Currently I just go to [www.shoutcast.com]("http://www.shoutcast.com") to listen

---

### Post by DapperMe17 on 2010-12-23
Yes, we'll find a solution in short time.

---

### Post by jgcamp99 on 2011-01-10
This is driving me batty in Exaile, I can load them manually the http's as new playlists, but the shoutcast radio listing won't refresh the list of stations. Maybe because it has over 44,000 radio stations, it freezes or just takes a long time to refresh ? Don't right click on refresh, it breaks it.

---

### Post by vector_force on 2011-01-10
It's clear now.

The new API's license agreement forbids third party software from using it.

I can always use IceCast or use the Shoutcast website for playing live streams.

---

### Post by kingsqueak on 2011-01-15
That just sucks....

This was one of those "minor" apps that I use pretty much constantly.

Thanks to the author for doing it, it was perfectly useful.

---

### Post by perezomail on 2011-02-08
[http://code.google.com/p/rhythmbox-shoutcast/](http://code.google.com/p/rhythmbox-shoutcast/)
i used the above in the rhythmbox plugins folder and opened the setup.sh file in terminal had to click the plugin check mark and restart the computer for it to work all the way perhaps you can jury rig the mentioned link to work with tunapie some how but rhthmbox also has a pandora plugin and such there is a way the above can make a favorites list to export also

---

### Post by weedeater64 on 2011-02-16
I just figured out a solution, sort of.  Go to shoutcast, do a search for whatever, in my case I was looking for coast to coast am streams.  click on a link, and instead of open with, click save as,  and you can save the .pls  rename the prefix to something of your choice, I use the station or site name then what I do is  mplayer -playlist file.pls

---

