---
title: "Rhythmbox Problem- Files Missing"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by sroark on 2008-01-22
I added my music from my XP Partition files (55 gigs worth) and it all went fine, added nicely with no problems. Well, I booted to XP for a wile to convert some file types then booted back to Gutsy and started up Rhythmbox to add my newly converted tunes when my library starts counting DOWN in the number of artists/albums/songs until it got to nothing remaining. Now my library is empty. Anybody know why? Thank you.

---

### Post by banewman on 2008-01-22
Sounds like it might be permissions - in gutsy browse to the folder with your xp music and right click a music file - select properties from the drop down menu - then click the permissions tab - your user should be in the group with read permissions.
:)

---

### Post by sroark on 2008-01-22
K, I just did that and they all say "root" and they are all grayed out and won't let me change anything. I clicked something and it said "you are not the owner," however, I should also note that after around 10-15 minutes, the entire library started loading back in and is fine now. I'm assuming it will do it again the next time I reboot, it did do something like this this morning now that I think about it, I just had not put any effort into it then so it didn't bother me. Any idea how to change the permissions?

---

### Post by sroark on 2008-01-22
I just restarted 2 more times, and upon the first time opening rhythmbox, it erases all 7000+ files one by one until it reaches zero, then they came back a few minutes later, this is just annoying lol.

---

### Post by sroark on 2008-01-23
OK so I figured it out, the disk containing the files needed to be authorized and on the desktop, then it works. Which makes sense because Rhythmbox couldn't find the music because it wasn't open, then when it is open it finds it and adds it all back. So my new question is, how can I go about making that disk start up automatically when I start Ubuntu. Also, how can I go about making Rhythmbox start up automatically? Thanks.

---

### Post by richarglamb on 2008-01-28
[http://ubuntuforums.org/showthread.php?p=3996077#post3996077](http://ubuntuforums.org/showthread.php?p=3996077#post3996077)

This shows you how to launch a programme at startup.

---

