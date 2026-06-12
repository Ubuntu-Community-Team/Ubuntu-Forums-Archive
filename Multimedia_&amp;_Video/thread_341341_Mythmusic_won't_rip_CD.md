---
title: "Mythmusic won't rip CD"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by AndrewWalker on 2007-01-18
I'm having trouble getting the mythmusic package for mythtv working. Whenever I try to rip a cd I get a list of the cd contents ok but as soon as ripping starts, the disk is ejected.
When I run mythfrontend from a console I get the following message

error opening output file /var/lib/music/  whatever disk it is
error initialising flac encoder got return code 4

I've looked through the forum and google for an answer but got nowhere. 
Anyone got any suggestions?

---

### Post by Titus A Duxass on 2007-01-20
Make sure that the directory /var/lib/music exists, it is not created during the myth install.
Once you create it that will clear one of your problems.

For the other it looks like encoder problems, do you have the flac encoder installed?

---

### Post by Diadem on 2007-04-11
I had this problem as well, but it turns out my music folder /var/lib/music belonged to root - check that your music folder has correct permissions.

---

