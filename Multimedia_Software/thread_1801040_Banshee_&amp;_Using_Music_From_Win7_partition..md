---
title: "Banshee &amp; Using Music From Win7 partition."
date: 2011-07-09
forum: Multimedia Software
---

### Post by Waff1es on 2011-07-09
Hey guys!

Please forgive me for my ignorance on the subject but here's whats going on. I have a dual boot of win7 and Ubuntu and in my doc/music/pictures... ect folders, I have a symbolic link to my Music folder in my win7 partition. The symbolic link works and I am able to play music through a program called "Movie Player" when I double click on a file. 

When I opened up Banshee for the first time ever, I imported my Ubuntu Music folder (which contained the symbolic link) and as planned, my library was filled up with my library from my win7 partition. Everything seemed to be in order as the music pops up with the correct metadata and album art but, when I click on one to play it, nothing happens.  I do not get an error message either. It just seems to ignore the command :/

Ideas?

---

### Post by 11ghjones on 2011-07-09
My guess is when it tries to transverse the symbolic link it doesn't mount the partition by default, like Nautilus would.  Have you tried browsing to the folder in Nautilus, then opening up Banshee and trying to play it from the library?

---

### Post by Waff1es on 2011-07-10
I first tested the pathing to the folder before I opened up Banshee (if that's what you mean). While trying to get Banshee going, I was individually opening up songs (in Movie Player) and listening to them. If it's a mount issue I just find it weird that Banshee was able to do all the overhead (find the songs, album art, and metadata) but then falling short on executing the file.

**I should also note when I tried playing a song out of Banshee for the first time (an MP3) and Banshee even understood it was an MP3 and requested I download proper codecs, which I did.** 

Is there a media player that could do what I want? I'm not gravitating towards any because I'm new to Ubuntu.

---

