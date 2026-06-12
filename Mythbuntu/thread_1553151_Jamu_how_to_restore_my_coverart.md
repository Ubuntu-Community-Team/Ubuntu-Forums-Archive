---
title: "Jamu how to restore my coverart?"
date: 2010-08-14
forum: Mythbuntu
---

### Post by elgordo123 on 2010-08-14
How do I get Jamu put my coverart images back into /var/lib/mythtv/coverart (the original location before jamu does it's "insert explective here")?    

I went into mythtv-setup and deleted the storage groups for banner, screenshots, etc and jamu ran on the hourly cron job, but they are still not there. 

Everything is standard - videos in /var/lib/mythtv/videos and coverart SUPPOSED to be in /var/lib/mythtv/coverart.  

I have many coverart and found them buried and renamed in my home directory, but I would like to know what command to run to get Jamu to put them back?   I can always copy and rename but that take way too much time and if Jamu is going to do all this funky stuff it should be able to put things back.   I'm going to disable it in mythcontrol center after I get my files back.

Any help would be appreciated.  Thanks in advance.

---

### Post by elgordo123 on 2010-08-17
The more I look into Jamu the more I can't believe it is included as a default.   I dont mind programs copying or linking my files, but I have a lot of old movies that are not on IMDB or have coverart.   For this program to MOVE and RENAME my cover art is an outrage.  
  It really needs to be an option at install.  Not only does it move my images, but there seems to be no way to easily put them back - and worse than that - it puts them in the home directory, which is normally on a separate partition than the rest of the data.   
  I think more people dont complain because "you dont know what you dont know"...  Go ahead try to find the cover art that you spent hours finding initially.   I've been using mythbuntu for a very long time and just until recently I had to grab a cover art file and found it wasn't there!  Thank goodness for backups. 
 Sorry guys - Jamu sucks.  If it was an optional install and easier to configure and easy to undo the damage it caused, I would like it.   To rectify this, I've disabled it in mythcontrol center and renamed the jamu.py to jamu.fu which is more appropriate.

---

### Post by larsolav on 2010-08-17
Hi there. Mythtv and Jamu now get meta data, cover art, and fan art from [www.themoviedb.org](www.themoviedb.org). I had the same problem as you, as many children's DVDs weren't on there. My solution was to register with [www.themoviedb.org](www.themoviedb.org) and populate the database with some meta data and cover art. Then, the next day the cover art would automagically show up on mythtv. This way, when someone else loads their Dora the Explorer DVD they get some cover art as well (I have not have had the time to do fan art). I think that was the idea behind [www.themoviedb.org](www.themoviedb.org)...

---

