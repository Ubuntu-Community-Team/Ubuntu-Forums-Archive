---
title: "3d accel not working with proprietary ati drivers"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by unrulycow on 2006-11-12
I'm trying to get the proprietary ati drivers to work on edgy on my laptop (Dell Inspiron 6400), and having problems.  I followed the guide at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and got them installed (ie fglrxinfo shows the following, that I think is correct)
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8) 
but 3d acceleration doesn't work (glxgears runs like ***, etc.)
If anyone knows what I need to do to fix this, it would be very much appreciated.   Thanks.

---

### Post by arthur_kalm on 2006-11-18
I also have an Inspiron 6400. I installed the ATI drivers following [this]("http://www.ubuntuforums.org/showthread.php?t=257684&highlight=inspiron+6400+howto") howto. However, since my upgrade to edgy I have had some problems with getting Beryl and XGL to work. When I find a good solution I'll post back here. Try the linked howto for now.

---

### Post by arthur_kalm on 2006-11-20
Hmm I haven't really found a solution. I made a post [here]("http://www.ubuntuforums.org/showthread.php?p=1786200#post1786200"), so you can follow it and see if there are any developments. Personally, if I can't figure this out in a couple of days I'm going to go back to Dapper. It was significantly more stable.

---

### Post by Melcar on 2006-11-20
I (and many others) also have performance related issues with Edgy + ATI.  I'm using the newest ATI driver (8.31) on my 200M.  It "works" fine and I can run XGL/Beryl with no problems, but some 3D apps. suffer from severe lags (like screensavers); I never had this problem with Dapper.

---

