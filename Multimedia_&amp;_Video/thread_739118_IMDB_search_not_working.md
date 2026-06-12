---
title: "IMDB search not working"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by ctarmen2 on 2008-03-29
Hi,

I am very new to mythbuntu and just getting everything set up for my home theater. I am trying to get the IMDB searches working, but unable to. I go to settings and video manager and hit "i" it seems as if it is going out to search, but I never get anything back. This is what I see in the mythtvfront end logs:

2008-03-29 10:28:47.353 Movie Search: Executing '/usr/share/mythtv/mythvideo/scripts/imdb.pl -M tv=no;video=no 310 TO YUMA'
2008-03-29 10:28:47.753 0381849:3:10 to Yuma (2007)

2008-03-29 10:28:47.753 GetMovieList returned 1 possible matches
2008-03-29 10:28:47.753 Movie Data Query: Executing '/usr/share/mythtv/mythvideo/scripts/imdb.pl -M tv=no;video=no 0381849'
2008-03-29 10:28:48.578

It looks like it's successfully hitting IMDB and getting the information but just stops there. Any help would be greatly appreciated.

Thanks!

---

### Post by ctarmen2 on 2008-03-29
bump for help please!

---

### Post by warp99 on 2008-03-29
Do you have version 0.20 or version 0.21 installed? Also are all of your plugins (mythvideo, mythflix, mythweather, etc.) the same version. I would go into synaptic and check to see that all of the version numbers match. :)

---

### Post by ctarmen2 on 2008-03-29
Warp99,

Thanks for the info, I updated all of the plug-ins. Everything is the latest version. 

I am still getting the same results. I know that the search is returning with the correct IMDB #, but none of the information is being updated. I don't see any of the movie information including the cover, director, rating...

Thanks!

---

### Post by ctarmen2 on 2008-03-29
Ended up doing a reload of the system and everything works great!

Thanks!

---

