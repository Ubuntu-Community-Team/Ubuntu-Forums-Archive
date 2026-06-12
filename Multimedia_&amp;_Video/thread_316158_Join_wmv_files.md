---
title: "Join wmv files?"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by jhaquo on 2006-12-10
hi
id like to merge some WMV files, any ideas how please?


i tried with cat, it makes a big file of the size of all the small wmv's togheter, but when i play it it stops after the first file lenght

i hope you can help :)

---

### Post by jsandys on 2006-12-11
The first part of a WMV file is the header with file length and encoding info, you can't just cat them together.  WMV files are a proprietary format, if the files were MP3, OGG, AIFF, AU or WAV format there are a couple of programs that you can use to edit these files.

---

### Post by jhaquo on 2006-12-11
well there are plenty of windows apps that will get the work done, but ic ant use them using wine because of some missing files(which i installed but it still give me the same errors)

---

### Post by alphablue52 on 2007-02-27
You may use mencoder (from mplayer, in the multiverse repository), but the results seem to be a bit buggy sometimes.
If you want to give it a try, enter the following to a command line:

mencoder -oac copy -ovc copy -o NEWVIDEOFILE part1.wmv part2.wmv part2.wmv ...

or just
mencoder -oac copy -ovc copy -o NEWVIDEOFILE part*

If all video files are named in correct alphanumerical order.
Mencoder creates an AVI file, which is mostly playable for xine, vlc and mplayer, but sometimes I get an error from KPlayer (which bases on mplayer - strange, hm?) that my system is too slow, and the merged video is played really slow :-(

Did you had some success with windows video software and wine jet?

---

### Post by H.E. Pennypacker on 2007-07-06
I have the same question, and I would like to use GUI.

---

### Post by Mortuis on 2007-12-21
This command line method worked great for me. :-)

---

### Post by disturbedite on 2007-12-21
avidemux (2.3) supports wmv input but not output...you could join them with avidemux and export/convert them to a different format...

---

### Post by HonorSystem on 2008-05-21
the mencoder method above works, but as was mentioned, the results are buggy.  specifically, a/v sync is not perfect (video is playing back slightly faster than it is supposed to, and thus audio seems to "lag").

---

