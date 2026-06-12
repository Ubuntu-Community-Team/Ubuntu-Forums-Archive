---
title: "Wrong length of converted video-file"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by maol62 on 2006-10-25
I have converted an avi-file (with 5.1 ac3-sound) to a dvd compliant mpg-file, but when playing it in my stand-alone dvd-player, it seems like the length of the movie is just about half of the length of the origninal avi-file. So if the avi-file is 60 minutes, the dvd-player says that the movie is just 30 minutes. But then, when looking at the dvd-players display, I can see that it takes twice as long time for a second to increase, i.e. it takes two seconds for the dvd-player to go from 0:00:01 to 0:00:02. Its the same when looking at properties of the mpg-file, it also shows just half of the correct lenght of the movie. I have used ```
tovid -dvd -pal -in infile.avi -out outfile
``` to convert the file to dvd-format. Then I have used dvdauthor to create the dvd-structure, and finally mkisofs to create the iso-file. Anyone who knows what could be wrong?

---

### Post by Rhubarb on 2006-10-25
You might have some luck finding some info at:
[http://www.doom9.org](http://www.doom9.org)

It does indeed sound quite bizarre.
It could be something to do with one of the IFO files there, but it's been a few years since I last dabbled with DVD transcoding and editing.

---

### Post by user1397 on 2006-12-04
> **maol62 said:**
> I have converted an avi-file (with 5.1 ac3-sound) to a dvd compliant mpg-file, but when playing it in my stand-alone dvd-player, it seems like the length of the movie is just about half of the length of the origninal avi-file. So if the avi-file is 60 minutes, the dvd-player says that the movie is just 30 minutes. But then, when looking at the dvd-players display, I can see that it takes twice as long time for a second to increase, i.e. it takes two seconds for the dvd-player to go from 0:00:01 to 0:00:02. Its the same when looking at properties of the mpg-file, it also shows just half of the correct lenght of the movie. I have used ```
tovid -dvd -pal -in infile.avi -out outfile
``` to convert the file to dvd-format. Then I have used dvdauthor to create the dvd-structure, and finally mkisofs to create the iso-file. Anyone who knows what could be wrong?did you ever use makexml? because you need to create a compliant xml file so that dvdauthor can describe the correct disc structure, and finally you can use makedvd to burn the disc.

---

### Post by cornish on 2007-05-08
did you ever find a solution because I am having the same problem?

---

