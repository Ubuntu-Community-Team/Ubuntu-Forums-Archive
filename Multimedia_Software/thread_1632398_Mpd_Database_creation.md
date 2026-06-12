---
title: "Mpd Database creation"
date: 2010-11-27
forum: Multimedia Software
---

### Post by Dobbie03 on 2010-11-27
I have just installed MPD and Sonata, followed the instructions from here:

[http://www.webupd8.org/2009/10/mpd-sonata-powerful-audio-player-for.html](http://www.webupd8.org/2009/10/mpd-sonata-powerful-audio-player-for.html)

use the commands for creating a database (sudo /etc/init.d/mpd start-create-db) and this is what I get in the terminal:


```
dobbie@dobbie:~$ sudo /etc/init.d/mpd start-create-db
 * Starting Music Player Daemon mpd                                             
 * creating /var/lib/mpd/tag_cache... 
                                                                         [ OK ]
```

Is it creating the database or what?  I dont know what is happening, when I start Sonata nothing happens as far as music showing in the library.  Is there something else I need to do?

EDIT:  I think I sorted it, MPD seems to be updating in Sonata!!  Yay.

---

