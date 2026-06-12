---
title: "Qdvdauthor Error!! :("
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by damvcoool on 2006-08-08
ok when i was working on Breezy Qdvdauthor worked like a charm, but now it has this weird messeges


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=14024&stc=1&d=1155091552[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=14043&stc=1&d=1155124850[/IMG]

I have already tried removing it and purging it, and the installing it again, and nothing same with the dvdauthor, i have tried DVDstyler but is not compatible with my XML's I already have for this app :S :S and is too much work doing them again :S

someone could please tellme what i have to do


PS:sorry for my english :S
PS: I really need help!!!

---

### Post by samcompton on 2006-08-11
It's not an issue of upgrading from Breezy.  It must have something to do with one of the recent updates.  I had qdvdauthor working brilliantly until this morning when I went to use it and got the same error as you.  As far as that goes I can not make a DVD using any of the programs that I have had success with in the past (tovid, polidori, dvdstyler)  One of the updates must have done something that is effecting DVD creation regardless of application.  

If anyone knows what to do about this, I could really use the answer on this as well.

---

### Post by samcompton on 2006-08-12
I'm sorry.  I spoke too soon.  It is true that I had qdvdauthor working on Dapper until recently.  It also happens that I just recently figured out that I had been encoding files to PAL MPEG.  So I changed my settings to convert files to NTSC MPEG.  Evidently there is the problem.  Something in dvdauthor does not support the aspect ratio of NTSC MPEG.  I'm not sure exactly what I am talking about.  I found this on a google search:  [http://impressive.net/archives/fogo/1137602650.23440.46.camel@jebediah](http://impressive.net/archives/fogo/1137602650.23440.46.camel@jebediah)
So I tried encoding a file to PAL MPEG and creating a DVD with it in qdvdauthor.  Perfect.  No prolems.  Luckily I have a dvd player that plays PAL.  Hope this helps.

---

### Post by samcompton on 2006-08-13
OK.  I am learning by trial and error.  So I will keep adding to this thread for anyone else who is having trouble with this issue.  

The work around that I have figured out is to go ahead and create your DVD using qdvdauthor like you normally would up to the point where you see this screen.
[IMG]http://geocities.com/samcompton/Screenshot.png[/IMG]

Don't hit OK yet.  

Go to the temp directory for your DVD.  Open file  dvdauthor.xml with your text editor.  Find the line with  <video format="ntsc" aspect="2.21:1" resolution="720x480" />   and change 2.21:1  to 4:3  or 16:9  whichever you have created.  Save after changes are made then go back to qdvdauthor and hit OK.  That worked for me.  DVD turned out just like I intended.  I'm sure there must be a better fix for this problem but, it's not within my abilities.  For now this work around will do.

---

### Post by Rever75 on 2006-08-18
There is a fix for this problem you need to upgrade to version 0.1.1 this bug was fixed in this version. Does anyone know if Ubuntu plans on creating a deb for this version?

---

