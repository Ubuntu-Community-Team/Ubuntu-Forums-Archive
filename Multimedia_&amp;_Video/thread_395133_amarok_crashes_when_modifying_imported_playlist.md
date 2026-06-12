---
title: "amarok crashes when modifying imported playlist"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Skeorx13 on 2007-03-27
When I import a playlist from winamp in winXP into amarok in ubuntu 6.10 it pulls up the tracklist fine. But if I try to play the songs it won't find any of the files. This isn't a big issue as I can just find them in my collection in amarok and edit the playlist. However when I do so amarok crashes after a few seconds and gives me the dreaded kmail error. I understand that a lot of people get this error and no one ever knows how to get rid of it. That's fine, as long as someone can help me to prevent it from crashing in the first place. Sure I could just write the playlist down on paper while logged into windoze and the go into amarok and manually put in each track but it's a pain in the ***, especially when the list is over 100 different tracks. Can anyone help?

---

### Post by spin2cool on 2007-03-27
I'm assuming the playlist is an m3u file.  If you open it up in a text editor, you'll probably see that it contains a list of fiel locations like this:

C:\Documents and Settings\I\My music\mymusic.mp3

The problem is, that address is meaningless in linux, since there is no c drive, etc.  You may be able to use your favorite text editor to do a little find-and-replace to give the correct addresses of the music files.  (i.e. replace "C:\Documents and Settings\I\My music\" with "/media/music/")

---

### Post by Skeorx13 on 2007-03-27
hmmm... I may have to try that then. It might be a .pls file though. Would I have to be in windows for that or could I be in ubuntu and use gedit? Would the file actually show that text or would it be all jumbled with computer language?

Edit:
Just made a quick playlist file here at work and I can edit both .m3u and .pls in windows. I'll try it in ubuntu when I get home and let you know if it worked.

---

### Post by dreadlord_chris on 2007-03-27
They are text files - and yes, you can edit them in Ubuntu

---

### Post by Skeorx13 on 2007-03-27
Woot! All I had to do was change the directory info. I edited a small playlist manually but then I poked around in the menu and found "replace." Opened the big playlist, replaced the old directory info with the new info and fixed 100+ songs in a split second. Fan-tastic. They work perfectly now. Thanks guys.

---

### Post by rahimveron on 2007-08-27
Yes this helped me a lot. I had a large number of m3u playlist and i never thought those were text files, & can be edited!!!  Just used find and replace in text editor and i have all my plalist working under ubuntu.

---

