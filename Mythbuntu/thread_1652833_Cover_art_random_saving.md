---
title: "Cover art random saving"
date: 2010-12-25
forum: Mythbuntu
---

### Post by nightwar on 2010-12-25
Hello. Been using Mythtv for a few years. 

I have a front end and back end seperate and a samba server.

When in mythvideo, I edit the metadata, and then hit W to grab the info and cover, sometimes it will save, other times it will write a 0 byte file.  Permissions are correct, otherwise the ones that work would not save.

Im running 10.10 and 0.24

my frontend was just re-built today from the CD installer.

Some logs from mythfrontend.log:

2010-12-25 18:02:32.541 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Ghostbusters
2010-12-25 18:02:32.975 Returning Metadata Results: Ghostbusters 0 0
2010-12-25 18:02:34.190 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 620
2010-12-25 18:02:34.644 Returning Metadata Results: Ghostbusters 0 0
2010-12-25 18:02:34.793 Metadata Image Download: [http://hwcdn.themoviedb.org/posters/81f/4bc90a2a017a3c57fe00381f/ghostbusters-original.jpg](http://hwcdn.themoviedb.org/posters/81f/4bc90a2a017a3c57fe00381f/ghostbusters-original.jpg) ->/mnt/storage/posters/620_coverart.jpg
2010-12-25 18:02:38.564 Metadata Image Download: [http://hwcdn.themoviedb.org/backdrops/813/4bc90a29017a3c57fe003813/ghostbusters-original.jpg](http://hwcdn.themoviedb.org/backdrops/813/4bc90a29017a3c57fe003813/ghostbusters-original.jpg) ->/mnt/storage/fanart/620_fanart.jpg



That resulted in a 0 byte file:(on the samba share)

-rw-r--r--   1 rich  wheel        0 Dec 25 22:06 620_coverart.jpg



----------------

I then remove the 0 byte file, hit W again on the frontend and it works:

-rwxr--r--   1 rich  wheel  1054617 Dec 25 22:08 620_coverart.jpg





here are the logs for the successful one:

2010-12-25 18:04:17.514 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 620
2010-12-25 18:04:18.034 Returning Metadata Results: Ghostbusters 0 0
2010-12-25 18:04:18.210 Metadata Image Download: [http://hwcdn.themoviedb.org/posters/81f/4bc90a2a017a3c57fe00381f/ghostbusters-original.jpg](http://hwcdn.themoviedb.org/posters/81f/4bc90a2a017a3c57fe00381f/ghostbusters-original.jpg) ->/mnt/storage/posters/620_coverart.jpg

---

