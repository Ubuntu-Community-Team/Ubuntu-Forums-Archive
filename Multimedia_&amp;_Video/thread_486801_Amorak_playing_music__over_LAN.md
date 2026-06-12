---
title: "Amorak playing music  over LAN"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by theredmoose on 2007-06-28
HI there, 

I have been trying out different music players and Amorak seems to be the only one that is good set of features.  However I am having trouble getting Amorak to see my music collection.  I have a windows XP box that has all my music files and is sharing a drive.  I have configured a samba share and can navigate to the files using Nautilus.  But when I configure Amorak to scan the collection it will only allow me to navigate to the root share folder.  Not any further down into the file structure.  I wouldn't mind as this is where I want it to start scanning from but it will not find anything.

Does anyone have any ideas on how I could get Amorak to work over the LAN?  Does anyone else have a similar setup.  

I am running Ubuntu 6.06.

Thank you
the red moose

---

### Post by unimatrix on 2007-06-28
The easiest way to do that is to mount the windows share, so it will be seen as a normal folder.
Here's some short info on how to do that: [http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node13.html]("http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/di8k-debian/node13.html")

And by the way, it's Amarok, not "Amorak" ;)

---

### Post by theredmoose on 2007-06-28
Thanks for the spelling correction.  The thing is that I have already mounted the windows share as a normal folder and I can navigate through it using Nautilus.  So there is nothing wrong with the windows share as I can see it.

---

### Post by unimatrix on 2007-06-28
Hmm, I've just tested this myself and It really does refuse to play samba-mounted files.
Fortunately this is a well known problem, and there even seems to be a fix: [http://amarok.kde.org/amarokwiki/index.php/Samba]("http://amarok.kde.org/amarokwiki/index.php/Samba")

---

### Post by theredmoose on 2007-06-29
Thank you so much.  That worked perfectly.

---

