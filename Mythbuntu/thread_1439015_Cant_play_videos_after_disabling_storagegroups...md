---
title: "Cant play videos after disabling storagegroups.."
date: 2010-03-25
forum: Mythbuntu
---

### Post by geobre on 2010-03-25
Hi,

I disabled storagegroups by removing the storagegroup "video" and then I filled the path to my videofiles in mythfrontend. Everything worked fine. But after updating the db using Jamu and mythfrontend to get pictures and descriptions of moviefiles I cannot play the moives that has extra information (metadata) in mysql database.
Movies I have not been able to update, thus they have no pictures or anything, still works fine..
What is the problem? Do I need to remove all the storagegroups (for fanart, coverart etc..) also? Trying to start a movie, avi or iso, the mythfrontend just blanks for a few seconds and then returns to show the movie menu. 
Before I had the iso and the avi in two separate directories, and it worked fine. Now I putted everything in the same directory structure /var/lib/mythtv/videos/ and I tested it with several movies. It worked nicely. But after upgrading the metadata of the movies, the movies that has metadata refuses to start. I do not se why. I looked in mythfrontend.log, but nothing about this..
How to resolve this? Please advice. I use mythbuntu 9.10

---

### Post by geobre on 2010-03-26
Hi again,

I dubbeltestet with just renamning a videofile to another name and then updated inside mythvideo to get myth to pick up the changes. That way I lost all metadata of that video. Doing so, both avi and iso plays like nothing. No problem at all.

Noone knowing why myth behaives like this?
In short again, I just deleted storagegroup "videos" and left the rest intact. I changed in mythfrontend the path for where videos are stored from /var/lib/mythtv/ISO/ to /var/lib/mythtv/videos/ B4 I had ISO in a separate dir to make use of storage groups. Now I descided I didnt want to sort them like that, instead I have my own structure in /var/lib/mythtv/videos/ with subdirs like "Action" SciFI" "Drama" (for wife) and so on..

Strange thing, my setup works as long as the video file avi or iso does not have metadata like fanart and stuff, but after adding metadata I cant play it anymore.

Added:
Even disabling in settings- media - video - general (i think, I have to translate from my language) second screen "Videolist loads metadata" makes myth play video again. But that is not how I wanted it.. I like when it shows the info and fanart for movies when browsing. It makes it easier to select and more appealing to the eye.. now its just a grey list of names...

---

### Post by singedwings on 2010-05-24
To resolve this I think you need to reset the meta-data in the front end for the files that won't update properly. Something to do with not coping with the previous data about the files unfortunately. Also Jamu needs to have its config file setup properly for your folders etc.

Instead of using Jamu to mass update your library, try using the metadata lookup in the frontend.

---

