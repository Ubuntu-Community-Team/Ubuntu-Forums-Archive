---
title: "MythTV &amp; RTJPG convert to MPEG1 or MPEG2"
date: 2008-04-30
forum: Multimedia Software
---

### Post by jtrindle on 2008-04-30
I'm going bananas trying to figure this one out.  MythTV 0.20.2  (or whatever the Gutsy repository version is) and a Hauppage WinTV D123 card, generates enormous .nuv files with RJPG encoding.  Watching live TV, recording, and playing back the huge files works fine within MythTV.

How do I get this compressed with MPEG1 or MPEG2, (MPEG4?) or even generate them that way in the first place?  I have tried many of the solutions on the web and they assume the .nuv file is really a misnamed MPEG file.  Not true here.

Mencoder processes without error, and I get audio, but the screen is blank and green.

Thanks!

---

### Post by andrewc6l on 2008-04-30
Is this something that nuvexport ([http://www.mythtv.org/wiki/index.php/Nuvexport](http://www.mythtv.org/wiki/index.php/Nuvexport)) can do?

---

### Post by jtrindle on 2008-05-05
Thanks for the reply!

It turns out that the latest edition of nuvexport does not work with the MythTV in Gutsy (0.20).  However, if you go to 

[http://www.forevermore.net/files/nuvexport/archive/](http://www.forevermore.net/files/nuvexport/archive/)

then

[http://www.forevermore.net/files/nuvexport/archive/nuvexport-0.4-0.20080219.svn.tar.bz2](http://www.forevermore.net/files/nuvexport/archive/nuvexport-0.4-0.20080219.svn.tar.bz2)

does work!  I have successfully exported SVCD-compatible video and have done other formats with glitches.

I also found the settings needed to reduce the size of the nuv files as they record.

---

