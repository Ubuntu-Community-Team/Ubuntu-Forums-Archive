---
title: "exaile sorting issue"
date: 2010-02-24
forum: Multimedia Software
---

### Post by metalmaniac248 on 2010-02-24
iv recently been getting a problem with exaile, where by some of the artists are sorted incorrectly

for instance, Michael Jackson is in the J's and Johnny Cash is in the J's and the C's 

iv tried a fresh install but the music library remains even when i use ```
sudo apt-get purge exaile
```
and remove the > ~/.config/exaile  directory

can anyone advise what i can do to fix this


PS. I just realised that its quite obvious why Michael Jackson is being put in the J's (because of his second name) and the same with johnny cash. what i don't understand is why its only these two that are being organized in this way the rest of the artists are sorted by first name.

---

### Post by psabullen on 2010-08-24
I was having the same problem, but after a little poking around, I found a simple solution.

The problem is caused by a tag called "artistsort".  For some reason, Exaile automatically creates this tag for some albums in the format of <Artist's Last Name>, <Artist's First Name>.  I'm not sure why some albums were sorted this way while others were not, but I did notice that all of the albums that were sorted this way contained .flac files, so that's one possible (yet, unverified) guess.

The way to solve this problem is to right click on the artist's name in the Collection tab (or highlight all the tracks in the playlist and then right click), and select "Properties".  Go to the "Tags" tab and scroll down to "Artistsort".  Rewrite this tag in whatever way you want, press the "apply current value to all tracks" button to the right of the tag, and then press apply.  Then you're done!   The only downside is that you'll have to do this for every artist that is incorrectly sorted one by one.  Also, it doesn't work if you just remove the tag altogether - Exaile will automatically recreate it whenever it rescans the collection.

Hope this helps!

---

### Post by misterspider on 2010-10-08
Ok, here is another sorting problem with Exaile. This applies to sorting a playlist (not my library).

I have a Ministry of Sound mixed double CD, so track order is important. When I load it into Exaile as a playlist, it alphabetically sorts by artist name, which are all different. If I sort by track number, it sorts as 1,1,2,2,3,3 etc because it is a double album. If I sort by disc number, it sorts disc 1 by artist name alphabetically and then disc 2 by artist (and once again both discs are not in track order).

Surely there is an easy way to load the double album to play in correct track order for disc 1 followed by disc 2?

I would love an option to be able to highlight any tracks, right click and have a "sort these tracks by ..." function. 

Or Sort by one column, hold down Ctrl and click another column and have it sort by these two columns.

---

