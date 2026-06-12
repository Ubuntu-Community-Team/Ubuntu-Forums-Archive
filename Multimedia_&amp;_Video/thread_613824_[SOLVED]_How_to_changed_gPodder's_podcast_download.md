---
title: "[SOLVED] How to changed gPodder's podcast download folder"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by philidox on 2007-11-15
gPodder has been working great for me,  there has only been one small issue,  I cannot change the folder where all the podcast content is being downloaded to.  I get this error message every time 
"Error moving downloads There has been an error moving your downloads to the specified location. The old download directory will be used instead."  I am only 1 step away from my podcasting experience being perfect.  Any suggestions would be a big help

---

### Post by flashoux on 2007-12-07
Hi !
Close       gpodder
Open       shell
write       gedit .config/gpodder/gpodder.conf 
locate      download_dir=
and change it !

Reply me if problem fix !


Flashoux

------------------------------------------
The French Touch ! ;)

---

### Post by philidox on 2007-12-07
Thx alot that work perfectly.  Gotta remember those config files! This aint windows!  I did not think anyone had the answer to this question but once again thx, you rock man

---

