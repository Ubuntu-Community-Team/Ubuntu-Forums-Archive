---
title: "Looking for wmav1/wmav2 encoding ffmpeg"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by dasbooter on 2007-06-06
I have switched from suse linux that had compiled windows media audio encoding capability (wmav1,wmav2) into ffmpeg but cannot seem to find a package that has the same for Ubuntu feisty. If anybody knows how I can get support for encoding this way please let me know.

This works in suse:

ffmpeg -i /home/dasbooter/2nd_storage/movie.avi -acodec wmav1 -vcodec wmv2 -ac 2 -qscale 3 /home/dasbooter/1rst_storage/visual_media/movie.wmv

but gives this in Ubuntu:

Unsupported codec for output stream #0.1

With what I have seen in ubuntu I find it hard to believe that some clever person hasn't compiled in support for encdoing wma with ffmpeg. I have added in the medubuntu repository already.

---

### Post by dasbooter on 2007-06-17
bumporama I had to install suse in a virtual machine to get wmv support for encoding with ffmpeg. Somebody want to set me straight on this?

---

### Post by dasbooter on 2007-08-13
Still wanting to know

---

### Post by dasbooter on 2007-10-03
I guess your best bet is to compile from cvs. You can get an Idea of how to do it here [http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) .The latest svn will have wmav1 and wmav2 decoding and you dont even have to enable that option with ./configure. I would have synaptic open to install all the needed dependencies (just install the dev versions of all the libs that ./configure cant find). Good luck. Oh and a big thank you to myself :guitar:

---

