---
title: "Fanart for movies but not recordings"
date: 2014-03-29
forum: Mythbuntu
---

### Post by larsolav on 2014-03-29
Happy Saturday to all.

I have been running Mythbuntu 12.04 with 0.27.0+fixes for a while, and have noticed that the backend downloads fanart for the movies but not recordings (the art that shows up behind the text in the recordings menu). 

I have a storage group set up for the fanart, and I see fanart in the movie menu.  I have checked the storage folder, and no recording fan art is in the folder. I have checked the tack for "allow metadata lookup jobs". 

I can't find any obvious errors in mythbakend.log or mythmetadatalookup.log... Any one know a fix? Thanks

---

### Post by blm-ubunet on 2014-03-29
You need series & episode numbers (not blank entry) in the metadata for the tv show recordings.
Movies are value zero (I believe) or blank.

Only some listings sources provide the complete data..
I don't get series & episode data in the correct fields (or at all) so have to manually edit these values..
This allow causes the inetref to be missing or wrong.
I have taken to running the grabber script in terminal & manually searching for the inetref.

Changing the *post recording* metadata is not so straightforward.

---

### Post by larsolav on 2014-03-29
Thanks for the quick reply blm!
Funny thing is that for shows that has full metadata available, my system does not download the fan art.
For example, tomorrow I will be recording [this Adventure Time episode]("http://thetvdb.com/?tab=episode&seriesid=152831&seasonid=221091&id=2289921"), and my system is linking to this site and inserting correct series and episode numbers, but for the episodes of Adventure Time I have recorded, no fan art is downloaded. I am stumped.

---

### Post by blm-ubunet on 2014-03-29
metadatalookup seems to fail when there are multiple results

Try
```
/usr/share/mythtv/metadata/Television/ttvdb.py -i -d -l en -D "Adventure Time"
```
```
/usr/share/mythtv/metadata/Television/ttvdb.py -i -d -l en -B 152833
```

---

### Post by larsolav on 2014-03-31
Thanks again!
I bet that was the problem, multiple results, and some shows without season and episode numbers.
So, I went through my list of recordings, and for each show I picked an episode and pressed "e" and then to the metadata option. From there I could search the available online art for shows that had a database entry. For shows that did not include an season/episode numbers i temporarily put in season 1, episode 1 so that the script would search the database. Now I have cover and fan art for most of the shows and my Mythbuntu theme looks awesome! Thank you blm for pointing me into the right direction!
Cheers!

---

