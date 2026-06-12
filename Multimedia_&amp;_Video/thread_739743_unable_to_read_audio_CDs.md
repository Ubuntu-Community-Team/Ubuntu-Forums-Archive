---
title: "unable to read audio CDs"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Stang Ulysses on 2008-03-30
I'm running 7.10 and the system will not even read an audio CD. I *can*, however, play
dvd's on my Optiarc DVD device. The CDrom is loaded in /media/cdrom0. When I put an audio CD in, it shows on the desktop as CD-ROM Disk. If I go to open it, I get the CD creator. This happens no matter what audio CD I put in it, however, I can access DVD videos and data CDs.  I have tried Amarok, XMMS, Audacious, and quite a few other players.

HELP!!  :)

---

### Post by wolfen69 on 2008-03-30
go to system>preferences>removable drives and media>multimedia tab and check what is default for audio cd's.

---

### Post by Stang Ulysses on 2008-03-30
The "Play Audio CDs when inserted" command is "Sound-Juicer -d %d".  No matter if I try to play the CDs or just try and browse them, I do not see the audio tracks.

---

### Post by Stang Ulysses on 2008-04-02
Just to see what the difference was, I installed Mandriva One last night.  I had the same problem with it that is happening with Ubuntu.  I could not read audio CDs at all.  Thet were seen as blank CDs.  Could this be some kind of kernel issue?

---

### Post by aeiah on 2008-04-02
i had this problem with exaile recently, although it just asked me to download python-cddb, which is just for grabbing song titles etc. you could always try installing that and seeing if it does anything

sudo apt-get install python-cddb

---

### Post by Stang Ulysses on 2008-04-02
Thanks.  I have tried quite a few of the player apps available including Exaile, all with the same result:  "No Audio CD inserted".  These are commercial CDs not any that I have made.  Windblows plays them fine, it's just Linux I have had trouble with.

---

### Post by Stang Ulysses on 2008-04-04
As an FYI Update:  I just installed Ubuntu 8.04 beta, and the problem does not occur.  I am now able to listen to CDs and read data discs "out of the box", and with the HOW-TO that is posted elsewhere on this forum, I can play DVDs as well.

Thank you all for your help.  :)

---

