---
title: "How to create endless run DVD from mp4 file?"
date: 2012-04-13
forum: Multimedia Software
---

### Post by YigalB on 2012-04-13
I have an MP4 file.
I would like to create endless run DVD, with no menu, that will run in endless loop on regular home DVD player.
Any idea how to do that?

---

### Post by mc4man on 2012-04-13
Well you have to convert to dvd format, author it into a DVD_VIDEO structure, then you need to adjust the last 'post command', -  
1 Exit 
to 
1 (CallSS) Call the First Play PGC, resume cell 1

This will cause the dvd to restart at the beginning instead of ending (Exit

As far as the converting & authoring you should be able to find many posts on..

I'm not aware of any Linux specific apps to edit the Pgc's of a dvd_video file other than PgcEdit which has a linux version,  But the windows version running in wine is much easier to use

Basically laid out how-to in this thread concerning the same though in this case the OP was using dvd slideshow & wanted to create a looping dvd

Note that I don't fool around with dvd's now to the extent previously but really wasn't that hard to do. 
PgcEdit has older 'donation' free versions that will do this job quite fine

Old thread on, post describing using PgcEdit (Once you have a video_ts ...
[http://ubuntuforums.org/showpost.php?p=4654173&postcount=6](http://ubuntuforums.org/showpost.php?p=4654173&postcount=6)

a few screens
[http://ubuntuforums.org/showpost.php?p=4677141&postcount=12](http://ubuntuforums.org/showpost.php?p=4677141&postcount=12)

---

### Post by gtippitt on 2012-04-13
The DeVeDe program in the Multiverse repository will do this fairly easy.  I use it for any video format I want to convert to DVD.  Using it, you will create a menu DVD where the first entry starts automatically.  There is an option for each menu item to say if you want to execute the next menu item, return to the first menu item , or play the same item again.  

It is a GUI app in Python that front-ends the lower level video applications.  It will create an ISO file that you can then burn to DVD.  Until recently I didn't have a PC connected to my TV and amplifier.  I sometimes saved a bunch of music videos from YouTube, and then use DeVeDe to create an ISO to burn to DVD.  I can then play these DVDs to watch and hear on my TV and sound system.  I use the menu options in DeVeDe to set each file to play one after the other and return to the first and replay.

---

