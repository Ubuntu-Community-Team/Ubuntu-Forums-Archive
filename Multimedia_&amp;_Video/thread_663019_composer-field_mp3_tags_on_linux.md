---
title: "composer-field mp3 tags on linux"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by mcmirande on 2008-01-09
Hello everybody, 

I was trying to tag my mp3 files with Amarok, EasyTag and Picard, but I obtained tags only for name of songs, and disc, but I can't obtain info about "composer" of songs. In order to get info about "composer" I'm using now my double boot and WMP11... and I would like to do that without using Windows. I also (as a second choice) tried "mp3tag" and "Magic mp3 tag" for Windows (via Wine), but even these softwares fail short to get WMP abilities. 

I guess MUST be some Linux software to get complete tags for MP3 files... Someone can help me to find it out?, or suggest some no-Windows solution?.

Thanks very much.

Marcos

---

### Post by ron999 on 2008-01-09
Hi
There are two versions of id3 tags.
ID3v1 and ID3v2.

ID3v1 does not have a 'composer' field, but ID3v2 does have one.

When you use EasyTag to tag your mp3 files you can apply both types of tag to each file.
(Look in Settings > Preferences > ID3 Tag Settings - make sure that the correct boxes are ticked)

But some mp3 players and PC media players read the v1 tags and some read the v2 tags instead.

So even if you have correctly filled in all the v2 fields, including composer, it still might not show up - depending on which player you're using.

I know that XMMS and Audacious don't show the composer field.
But VLC media player shows all the fields if you look in View > Stream & media Info > Advanced information.

I have attached screenshots to show the difference between the v1 and v2 fields for one mp3 track.

---

### Post by mcmirande on 2008-01-09
mmm, thanks but I already had configured EasyTag to show ID3V2. The problem is not which info the program shows but which can obtain from the web.
When I search tags for particular mp3 files or complete discs, EasyTag recovers correctly all information from ID3V1 tags, but none from ID3V2 (although settings of program are set to show it)...

Thanks for your comments, Marcos.

---

### Post by ron999 on 2008-01-10
OK
EasyTag gets its info from an online CD database.
If the database doesn't have the info for all the fields then I guess you have to fill them in manually and save.
I don't know where WMP11 gets its info, perhaps it accesses a more detailed database.
8)

---

### Post by mcmirande on 2008-01-10
Yes... I guess the same... that the only difference is that WMP gets info from some (presumably) non-free (and most detailed) database.

Thanks for your help

---

### Post by mcmirande on 2008-01-19
Hi everybody

I found out that tags saved by WMP11 are not readable for Amarok. So, my request of tags on Windows not only is boring... also is completely useless. The best way to get (complete) tags directly from Linux is to complete this info manually from wikipedia (linked directly to Amarok).

Thanks again, Marcos.

---

