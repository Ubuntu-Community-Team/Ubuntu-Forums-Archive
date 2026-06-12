---
title: "ffmpeg error using dvd-slideshow"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by mpoole on 2008-02-07
I am trying to create a slideshow using dvd-slideshow.  I can't even run the simple example on the dvd-slideshow wiki.  I get this error in the logfile:

Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
[dvd-slideshow] ERROR during ffmpeg execution!

Do you know how to remedy this?

---

### Post by tjbonzo on 2008-02-24
From: [http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

"Note: There is a known issue with newer versions of ffmpeg requiring a different audio bitrate syntax which makes audio encoding fail. This is fixed in the Subversion Repository code."

The good news is that it is fairly easy to grab the SVN:

From: [http://sourceforge.net/svn/?group_id=100188](http://sourceforge.net/svn/?group_id=100188)
 svn co [https://dvd-slideshow.svn.sourceforge.net/svnroot/dvd-slideshow](https://dvd-slideshow.svn.sourceforge.net/svnroot/dvd-slideshow) dvd-slideshow

(assuming you have svn installed). 

This will give you a directory with an updated dvd-slideshow that does not have the problem. Good Luck.

---

### Post by tjbonzo on 2008-02-24
Or apparently, from a very good post on using dvd-slideshow:

[http://jcornuz.wordpress.com/2008/01/22/producing-a-dvd-slideshow/](http://jcornuz.wordpress.com/2008/01/22/producing-a-dvd-slideshow/)

You can just,
"One last thing: if your dvd-slideshow complains about “error during ffmpeg execution” when generating the .vob files, try changing ac3=1 to ac3=0 in /usr/bin/dvd-slideshow, line 561. It did the trick for me."

---

### Post by jjones22 on 2008-02-26
Thanks, this helped me a lot, but I had to change line 661 not 561.

---

### Post by AdNZL on 2008-02-29
Hiya I'm having exactly the same problem but am still pretty new to linux. I tried editing the slide show bin, but I can't save what I've changed because it say's I don't have permission. How do I save it? :(

---

### Post by AdNZL on 2008-03-01
Well after a bit of desperate mucking about I finally figured it out, and just in case there's some other poor noob like me out there this is what I typed into the terminal

gksudo gedit /usr/bin/dvd-slideshow

---

