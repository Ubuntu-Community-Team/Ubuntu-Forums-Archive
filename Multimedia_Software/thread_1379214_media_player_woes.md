---
title: "media player woes"
date: 2010-01-12
forum: Multimedia Software
---

### Post by althegud1srtaken on 2010-01-12
i just can't seem to find a decent media player for all my needs, which don't seem that demanding.  i want to be able to:

*load my library (over 20,000 songs)
*easily edit ID3 tags several at a time
*be able to search by genre artist album
*easily manage my ipod

and that's it

*old amarok versions did this but were unstable
*new amarok versions are way too bloated and skip when playing my music, not sure why
*rhythmbox also skips sometimes and only sometimes likes my ipod
*banshee is the only player that i have that doesn't skip, but i can't search by genre and it's really slow with my ipod.  i just deleated all the songs off my ipod shuffle and it took over half an hour.

can the amarok source code be compiled with less frills to make it faster? this is easy in gentoo, but i'm not sure about ubuntu.  or anything else be changed? i feel like it has some potential if i could slim it down.

or is there a better player i'm unaware of? and why would these programs be skipping? i can watch DVDs and video files just fine.  any advice would be very appreciated.

ps- my computer is an acer aspire one w/ a dual core atom CPU.  not exactly the fastest computer but there's no reason it should struggle to play MP3s

---

### Post by aeiah on 2010-01-12
although i dont have that many songs on my acer aspire one, i dont have any problems with exaile. i dont do much re-tagging but on my main pc my collection is 14,000. my computer didnt agree with the new v3 of exaile though. there's also quod libet which has very good tagging and might be worth checking out.

---

### Post by jasp.armstrong@gmail.com on 2010-01-12
Try SongBird. I'm in the same boat. I just got a 50Gb external and moved all my music and videos to it. Now I'm migrating my music from formerly Windows Media Player to a new media player in Ubuntu. I have tried Amarok and RhythmBox and not impressed with either. I just tried SongBird and so far am pretty happy with it.  It's has all the functionality that you listed.

---

### Post by althegud1srtaken on 2010-01-13
thanks for the tip on exile! it's almost exactly what i'm looking for.  i havn't tried it with my ipod yet, but it looks like it should work

two problems with it:
it stuggles with my full collection but as soon as i narrow it down with a search everything is fine

the search doesn't include genres.  the code for this is really simple though, so i fixed that.  infact, looking at the code you can even see a comment that the authors want the search items to be user-defineable.  the best option in my opinion would be to search all the columns being displayed, but i havn't looked at the code enough to do this.

the simple fix is to get the latest source: [http://www.exaile.org/downloads](http://www.exaile.org/downloads) i used 0.3.0.2

open the file xl/trackdb.py and look for```
SEARCH_ITEMS = ('artist', 'albumartist', 'album', 'title')
``` (line 54 in 0.3.0.2)
and change it to ```
SEARCH_ITEMS = ('artist', 'albumartist', 'album', 'title', 'genre')
``` or add any other fields you want and save the file.  then in the source code's base directory open a terminal and run ```
make clean && make
```and then```
sudo make install
```

notes: i got a few errors on make install, but they don't seem to be too important as everything runs fine.  also, make install will overwrite any existing files, so there's no need to un-install any existing versions.  this also means that if anything screws up, your existing version is gone.  also, if you initially used the package manager to install this it will try to update newer versions on top of your modified version, so you will need to modify the [new?] code again, re-compile, and re-install

---

### Post by althegud1srtaken on 2010-01-13
*UPDATE*

well before i did all this exaile saw my ipod in a devices tab on the side, which i'm assuming is what it's supposed to do.  i only tried this once but saw that it looked functional though i never actually tried to manage anything on my ipod.  now it sees it in the device manager, but never loads anything to that side tab.  i've reset my ipod with new firmware, re-installed the original exaile package, deleted everything and started over, etc.  after everything i can think of i can't get it to like my ipod, and i'm not finding any useful info in these forums or through google.  any ideas?

---

