---
title: "can anyone recommend a good player for a large (~900GB) music collection?"
date: 2011-05-07
forum: Multimedia Software
---

### Post by wim.glenn on 2011-05-07
hi there, i've recently installed 11.04 and am giving banshee a shot.  it seems pretty good although has crashed a few times.  but when i import my music folders (about 900GB,  175,000 items .. and growing..) it takes days.  that's not such a big problem because it only needs to be indexed once, i assume, ... but the UI is very slow now - so that clicking on an album can take several seconds to bring up the tracklist.  also typing into the search box there is a large delay before the matches are shown.  is this just to be expected for such a large db?  i recall i had google desktop indexing and returning results almost immediately back on winblows ..

other ones i have tried include rhythmbox , amarok, songbird ..  but have not found any of them to be stable and simple enough to my liking.  

can anyone recommend a good player , my essential requirement is a fast and efficient indexing - with tag support would be grand, but just based on filenames is ok too.   drag and drop into a play queue like rhthmbox had would be nice.  

thanks!

---

### Post by |{urse on 2011-05-07
[http://digg.com/news/technology/One_Terabyte_iPod_within_5_years](http://digg.com/news/technology/One_Terabyte_iPod_within_5_years).

lol this was dug 6 years ago, I'm assuming you mean software =) Banshee would rock that. Also give Moovida a try, it's a little different but it seems to handle my terabyte of media without (too many) problems.

---

### Post by rlj1965 on 2011-05-07
> **|{urse said:**
> [http://digg.com/news/technology/One_Terabyte_iPod_within_5_years](http://digg.com/news/technology/One_Terabyte_iPod_within_5_years).

lol this was dug 6 years ago, I'm assuming you mean software =) Banshee would rock that. Also give Moovida a try, it's a little different but it seems to handle my terabyte of media without (too many) problems.



Moovida is for Windows

---

### Post by Rasa1111 on 2011-05-07
No rlj1965, Moovida is installed in 2 of my Ubuntu machines.
Look in the software center, there it is. ;)
Though I wouldnt want to use it for my huge music collection. 

Anyway..

OP, give Clementine a try, it handles my 100+ GB's easily. 
and Ive read of others with larger using it no problem.

Best ive found yet, awesome app.
If youve not checked it out, give it a try! 

Good luck.

---

### Post by maghoxfr on 2011-05-07
The best player I've found in Ubuntu is Clementine. Easy, simple, fast. I need a player for playing music, period, Clementine is awesome.

---

### Post by Rasa1111 on 2011-05-07
> **maghoxfr said:**
> The best player I've found in Ubuntu is Clementine. Easy, simple, fast. I need a player for playing music, period, Clementine is awesome.

Definitely! :D 
and it fits into Ubuntus sound menu  (Like rhythmbox or banshee) beautifully. 

 One of the first apps. I install after a fresh OS install.

---

### Post by K_45 on 2011-05-07
```
sudo apt-get install cplay mpg123
```

2MB media player. No need for a bloated GUI . . .

---

### Post by m_duck on 2011-05-07
You can (or at least used to be able) to use Amarok, but with MySQL as the backend instead of whatever it uses by default (SQLite?). From what I've read, this should be faster for large libraries.

Alternatively, have you tried anything lighter which is based on folder structure / filenames instead of tags like K_45 mentioned? I could add mocp, cmus and mpd to the list.

Note that my music collection is relatively small (heck, my video collection is *relatively* small!) so these are purely suggestions and not based on large-library experience :p

---

### Post by slooksterpsv on 2011-05-07
I wonder how Exaile would handle that much music. I know for my measly 8.5GB Music collection it does well (sorry I have specific music I like, not everything that was ever made ;P, unless you're a DJ which I understand then)

Hmmm

---

### Post by Rasa1111 on 2011-05-07
> **slooksterpsv said:**
> I wonder how Exaile would handle that much music. I know for my measly 8.5GB Music collection it does well (sorry I have specific music I like, not everything that was ever made ;P, unless you're a DJ which I understand then)

Hmmm

Exaile failed miserably with my 100+ GB's. 
Clementine handles it great though.
and some have 'wider' "specific" tastes in music than others, 
that doesn't mean "everything ever made". lol :rolleyes:

---

### Post by maghoxfr on 2011-05-08
> **Rasa1111 said:**
> Definitely! :D 
and it fits into Ubuntus sound menu  (Like rhythmbox or banshee) beautifully. 

 One of the first apps. I install after a fresh OS install.

Agree, I "discovered" Clementine not so long ago. But given the fact that Rhythmbox, Amarok, Banshee etc. all take a few seconds to do tings, and sometimes freeze or fail at doing what I want and Clementine doesn't, it became my only music player. One thing I love is the way it handles the tags of the songs/albums, you change it and it's done (fascinating, right?). The automatic search engine to fetch album covers and song tags it's awesome too. I'm aware that those features are not unique to clementine, but in my case it's the only player that handled them in a successful and fast way.

---

### Post by oldos2er on 2011-05-08
gmusicbrowser

---

### Post by |{urse on 2011-05-13
+1 for Clementine, very nice.

---

### Post by wim.glenn on 2011-05-16
ok i've downloaded and i'm trialing clementine for a few weeks.. very nice so far , thanks guys !

---

### Post by halovivek on 2011-05-16
Do you have whole world musics in your system ?
This is the first time i come across like this.

---

### Post by wim.glenn on 2011-05-18
well, i really like music! i probably have an album from every country in the world , so in a way you could say i have the whole worlds music :P  but i think even at 1TB i'd probably still only have < 0.1% of all the world's recorded music !!

---

### Post by wim.glenn on 2011-06-02
hi all, i've given clementine a good run for the last couple of weeks, and it's the best thing i've used so far but it still has a couple of issues for me - i was wondering if anyone had ideas or solutions .. 

1. the indexing works well, except for the case where some files don't have tags - i would like these to show up in search results if the search content is in the filename and at the moment those files are not found.  i noticed this when some versions of songs i knew i had were missing from the search output even after a full library rescan.  so i guess it is indexing by tags, and i could not find any obvious setting to include filenames in the search

2. sometimes when a new song starts playing the sound output is horribly distorted and aliased.  if i start playing the track from the beginning again it goes back to normal.  i'm using ALSA and Codec: Realtek ALC889A on Intel HD Audio chip, fiddled with codecs and sound engines but couldn't fix anything yet 

3. an alternative solution to problem 1. would be to tag those files that are missing tags, this would have to be automated due to the size of my music collection.  but maybe such software actually exists already, since i have seen the amazing things 'shazam' can do with using acoustic fingerprints.. anyone?

---

