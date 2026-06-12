---
title: "yet another music player post"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by thebloggu on 2008-02-02
i used to use itunes in windows but now i use ubuntu but haven't find the music player/library manager that fits perfectly. i like the way itunes organizes the library. the most close to this is exaile but it seem to have problems with music tags (////////// shows instead of artist names) and the main window show primarily the playlist while i prefer for it to show the library (i know i can change this with themes but could only find one). if you can solve the problems with exaile i'll use it or show another music player (tried listen, exaile, banshee, amarok, rythmbox, bmp, muine, kaffeine, songbird)

---

### Post by lluisanunez on 2008-02-02
[aTunes]("http://www.atunes.org/") is Java based and looks a lot like iTunes
Still I'm using GTKpod, initially meant to manage the iPod but wich manages nicely my local library, ID3 tags, etc...

---

### Post by schallstrom on 2008-03-10
I just discovered atunes. It's so neat! It's really the most perfect open source audio player I ever used. How does it come that there is no Ubuntu package? Is there a way to get it in hardy?

---

### Post by raul_ on 2008-03-10
> **thebloggu said:**
> i used to use itunes in windows but now i use ubuntu but haven't find the music player/library manager that fits perfectly. i like the way itunes organizes the library. the most close to this is exaile but it seem to have problems with music tags (////////// shows instead of artist names) and the main window show primarily the playlist while i prefer for it to show the library (i know i can change this with themes but could only find one). if you can solve the problems with exaile i'll use it or show another music player (tried listen, exaile, banshee, amarok, rythmbox, bmp, muine, kaffeine, songbird)

Amarok should do the trick

---

### Post by schallstrom on 2008-03-10
If you don't want to install all the KDE libraries in order to use amaroK, you could have a look at listen. It's Gtk based and it came close to perfection for me before I discovered aTunes.

---

### Post by wsamh on 2008-03-10
how do you install atunes. I downloaded the file. But what do you do next.

---

### Post by schallstrom on 2008-03-10
I tried to install atunes  on Ubuntu as described here: [http://www.atunes.org/docs/linux-howto/linux-install.html](http://www.atunes.org/docs/linux-howto/linux-install.html)

But it didn't work for me. There is coming up the language chooser for installation but the application seems to crash and freeze immediately. I use aTunes on my Windows box and listen on my Ubuntu laptop.

---

### Post by thebloggu on 2008-03-10
do you have java and mplayer installed?

---

### Post by schallstrom on 2008-03-10
Aah, I found out what the problem was!

The howto at the link I posted before is working, you just have to update your alternatives like this:
```

sudo update-alternatives --config java

```
and then choose Sun's Java.

On my system it was using GCJ by default which doesn't seem to be able to handle the aTunes java code.

---

### Post by schallstrom on 2008-03-10
> **thebloggu said:**
> do you have java and mplayer installed?

See above.

---

