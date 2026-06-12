---
title: "PiTiVi and large MPEGs: Bad match?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by charlie cat on 2010-05-02
I have some MPEGs that don't work in Windows Movie Maker.  I get an error along the lines of "An interface has to many methods to fire events from".  Strange.  So, I decided to try it out in Linux (Specifically, Ubuntu Lucid).  Importing them into PiTiVi, I get a different, strange error message: "Problem:Timeout while analyzing file.  Extra information:Analyzing the file took too long."
The only related issue I can find on Google is here: [http://old.nabble.com/Cut-slice-razor-keyboard-shortcut-td27763377.html](http://old.nabble.com/Cut-slice-razor-keyboard-shortcut-td27763377.html).
Any ideas?
I got the files to import and play in Kino.  These files are quite large (136.7 MB), which may be causing the timeout error.

---

### Post by no2498 on 2010-05-03
try tragtor

[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)

hope this helps

---

### Post by charlie cat on 2010-05-03
Thanks!  I converted it to a .OGG and I can now import it easily.  traGtor also solved another problem I had with Windows Media Converter, which would shut down as soon as you did anything... Hooray for Linux!
Also, I found some actual documentation of this error in the [PiTiVi Manual]("http://www.pitivi.org/manual/PiTiVi%200.13.4%20manual.odt") on the second last page.
I may still have to use Kino, though.  I've started a [new thread]("http://ubuntuforums.org/showthread.php?p=9228946") with my next set of problems...

---

### Post by conradin on 2010-05-03
Ive used pitivi with files (MPEG and AVI ) around 2 gig in size no problems.

---

### Post by charlie cat on 2010-05-04
I guess it could be just a matter of performance.  The computer I'm using isn't exactly new...
Also, I believe there are different types of MPEG files, MPEG-1 and MPEG-2, so that may be what's causing the difference.

---

