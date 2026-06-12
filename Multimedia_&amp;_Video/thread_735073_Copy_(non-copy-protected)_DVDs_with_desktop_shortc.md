---
title: "Copy (non-copy-protected) DVDs with desktop shortcut"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by sparkguitar05 on 2008-03-25
I have a bunch of DVDs of myself as a little kid.  My mom wants to make copies of these DVDs and give them to friends.  I want to know if there's a way to put a shortcut on the desktop that will copy a DVD.

These are home-made DVDs, so I don't need to worry about shrinking or copy protection.  I just want to be able to put the original DVD in the top drive, put the blank DVD in the bottom drive, and just push a button and be done with it.

I'm guessing there's some way to do this in the command line and then put a shortcut to that on the desktop, but I have no idea how to do this.  I've only been using Linux for two days so forgive any ignorance. 8)

---

### Post by pseudo-random on 2008-03-25
Put this in a text file and save it to your desktop as ripdvd.sh

> mencoder dvd://1 - o rippedmovie.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4

You will need to have the CSS codecs as well for encrypted DVD's. You can get them by installing MEDIBUNTU.
dvd://1 assumes chapter 1 but it could be different...
This method is fastest and the end quality is good when weighed against the filesize (700-900MB)

---

