---
title: "How to get the length of a video from the cli"
date: 2011-12-15
forum: Multimedia Software
---

### Post by btolman on 2011-12-15
I'm trying to figure out how I can tell the playing time for video (flv) from the command line. I can get the file size, but that's not the goal.

See, I'm converting user uploads from mov/mpeg/etc using a command line, and then uploading that to filesystem, and writing stats to the db. I can't trust the user imput the correct time (silly lUsers), so I need to figure it out.

Thoughts? Suggestions? Jokes?

Thanks in advance.

---

### Post by cgroza on 2011-12-15
I found this and apparently you can use FFmpeg to read the meta-data from the file:
[http://forums.devshed.com/php-development-5/how-to-get-length-of-flv-video-using-php-418100.html](http://forums.devshed.com/php-development-5/how-to-get-length-of-flv-video-using-php-418100.html)

There should be something about it in its manpages.

This also:
[http://code.google.com/p/phpvideotoolkit/](http://code.google.com/p/phpvideotoolkit/)


It is a wrapper for FFmpeg if you want to do it in php.

---

### Post by stonewilson on 2011-12-16
I remember an media player called baofeng(yes, it's a Chinese media player) can show the length of all video files after you brodcast one file with it.

---

### Post by FakeOutdoorsman on 2011-12-16
There are several methods using FFmpeg shown here: [Get the length of a song?](http://ubuntuforums.org/showthread.php?p=9807598#post9807598)

---

### Post by nothingspecial on 2011-12-16
Thread moved to Multimedia & Video. Title changed to reflect the subject.

---

