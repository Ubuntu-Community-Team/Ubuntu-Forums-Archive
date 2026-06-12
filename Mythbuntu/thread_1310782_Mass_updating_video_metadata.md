---
title: "Mass updating video metadata"
date: 2009-11-02
forum: Mythbuntu
---

### Post by fenian on 2009-11-02
If you are like me and have a large number of video files you probably don't want to go though manually updating the metadata in watch videos.You can use the Jamu script to automatically grab the info.Make sure you first set up the storage groups on the backend (mythbackend setup>storage groups).To run the mass update open a terminal and enter...

> /usr/share/mythtv/mythvideo/scripts/jamu.py -M -V -I

It will go through your video files and grab metadata for them.Occassionally it will ask you to specify from a list the exact title (when the title has more than one possible matches).

More info on Jamu can be found [here]("http://www.mythtv.org/wiki/Jamu").It seems to be a powerful script that can do much more than the simple usage above.

---

### Post by Kereszte on 2009-11-19
Last week, I installed Mythbuntu 9.1 and everything works wonderfully except that jamu is not in the mythvideo/scripts folder.

Since it's included in MythTv 0.22, I should automatically have it, correct?

Thanks
AJ

---

### Post by utar on 2009-11-19
Jamu is included with 9.10.  I'm not in front of my box at the moment but try typing "locate jamu.py".

If you have any trouble with jamu I can recommend:

[http://code.google.com/p/fill-mythvideo-metadata/](http://code.google.com/p/fill-mythvideo-metadata/)
[http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl](http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl) 

This works with multiple naming conventions and films as well as TV episodes.


Utar

---

### Post by Kereszte on 2009-11-19
Thanks :D

---

### Post by skiMJ on 2009-11-20
I've updated to 9.10 with myth 0.22 and I couldn't seem to find the jamu.py script. 'locate jamu.py' didn't return anything. My /usr/share/mythtv/ directory didn't have a mythvide directory.

It sounds silly now but I finally figured out that I didn't have the mythvideo package installed on my backend, only the frontend. These scripts only come with the mythvideo package. But now I'm even more confused, I'm pretty sure that I've read that myth 0.22 now includes mythvideo, why is it a separate package in ubuntu?

---

### Post by liquidox on 2009-11-20
I've spent a lot of my free time in the last couple weeks to perfect my MythTV media center.

In my experience, Jamu is not the fastest way of updating movie metadata, my favourite method for mass updating is now:

1) Use/run mythvideo-scanner [http://mysettopbox.tv/phpBB2/viewtopic.php?t=19082](http://mysettopbox.tv/phpBB2/viewtopic.php?t=19082) It can remove a lot of crap from filenames, downloads the main poster and updates the DB.

2) Go into gallery mode and view your Movie folder, you should now see all your movies with covers, now you can just use whatever button you've assigned to TMDB to quickly get the full metadata/fanart/info for all your movies.

Jamu is still the best way to get full info and art on TV shows though, but for movies it's not that great at finding the correct matches, in my experience.

---

