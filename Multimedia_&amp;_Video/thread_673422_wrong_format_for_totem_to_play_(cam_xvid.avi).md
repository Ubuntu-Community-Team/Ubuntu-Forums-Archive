---
title: "wrong format for totem to play (cam xvid.avi)"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by broekskw on 2008-01-20
trying to get some video files to play in totem but keep getting error code that said 

Totem could not play 'file(file name) CAM Xvid.avi'
There is no plugin to handle this movie.

did a search and tried many fixes but still nothing, also tried to install w32codes but get this error message from a terminal window

any suggestions:guitar:

---

### Post by banewman on 2008-01-20
Seems like you haven't enabled the universe and multiverse repositories in your sources list.
:)

---

### Post by kostkon on 2008-01-20
> **broekskw said:**
> trying to get some video files to play in totem but keep getting error code that said 

Totem could not play 'file(file name) CAM Xvid.avi'
There is no plugin to handle this movie.

did a search and tried many fixes but still nothing, also tried to install w32codes but get this error message from a terminal window

any suggestions:guitar:

In order to be able to install the Windows codecs package (i.e. *w32codecs* package), you have to add the [*Medibuntu*]("http://medibuntu.org/") repository to your software sources list. Please follow [these instructions on how to add it]("http://help.ubuntu.com/community/Medibuntu").

---

### Post by broekskw on 2008-01-20
ok banewman running ubuntu 7.10 under system>admin>syanptic>setting>repositorys???

then what do i need to select??

thanks

---

### Post by banewman on 2008-01-20
Then under the "ubuntu software" tab check all boxes except source code. Then close and click reload.
:)

---

### Post by broekskw on 2008-01-20
kostkon trying to follow instruction to install but link to page will not open any other link to this guide??
:popcorn:

---

### Post by broekskw on 2008-01-20
found another post with google and tried to input under system>admin>software source>3parts software> add then input the following two command lines 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

then reloaded but keep getting this error

looks like it did not take?? correct'

---

### Post by kostkon on 2008-01-20
> **broekskw said:**
> found another post with google and tried to input under system>admin>software source>3parts software> add then input the following two command lines 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

then reloaded but keep getting this error

looks like it did not take?? correct'

This is  the old url of the Medibuntu repository and is not working anymore.

It is strange that you cannot access the links I have given you. You could clear the cache of your browser and try again.

---

