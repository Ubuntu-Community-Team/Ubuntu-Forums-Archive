---
title: "Can Not Transfer Music To iPod"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Source4 on 2007-11-06
Hello,
I have been using Rythmbox on my 7.10 and I could always drag and drop my song into my iPod.
But I just "Returned my iPod to factory settings" and not when I try to drag my songs to the iPod I get this error message,

Error transferring track

Could not open file "/media/iPod/iPod_Control/Music/f33/13 - Blue Jay Way.mp3" for writing.

Why is this? So as of right now my iPod is worthless, there is nothing on it, so if anyone can help me, that would be amazing!!
ps. I re-setted it on a Mac if that helps.

I also have tried to run it on gtkpod and Amarok, neither of which worked at all either.

---

### Post by usererror on 2007-11-07
have you had any luck with this?  I Just plugged in my ipod for the first time and Rythmbox is playing my music on my ipod through my PC speakers.  AWESOME!  Hell, there's no reason really to keep my music on my PC anymore!!!

---

### Post by Clay Ferguson on 2007-11-25
Has anyone solved this problem yet??? I have an iPod Nano which is also able to be 'read' by the music player (i.e. can play songs) but if I dare try to drag a file onto the iPod, I get the error "Error Transferring Track" - "No space left on resource", even though there is plenty of space on the iPod.  Also my machine completely freezes.  I have to completely reboot in order to even get mouse or keyboard back.  Looks like at this time, Ubuntu actually does NOT support iPods, if you ask me.

---

### Post by Clay Ferguson on 2007-11-25
UPDATE - PROBLEM SOLVED: 

Here is how I solved the problem.  I opened the iPod in the "File Browser" (available via desktop icon) and looked for files eating up space.  Remember the 'dh -h' command can allow you to confirm this is the problme. In File Browser I found the iPod_Control/music folder had tons of files NOT being shown in the player.  Just sitting there eating up space. So I just deleted them using the File Explorer.  That cleanded up everything.  BTW: Normally you don't want to jack around with files in there manually however.  Use the Music Player to copy files to iPod! ;-)

Anyway now iPod works fine under UBUNTU!!!!  Yessss!

---

### Post by pulsewidth on 2007-11-30
I've actually had decent luck with Floola. It's available fromGetDeb,but actually got it from  Floola.com. I may try rhythmbox again,though. There's also a FUSE iPod filesystem implementation that might be kind of cool as well.There are a few other programs out there that can support iPods as well:gtkpod and hipo come to mind...

---

