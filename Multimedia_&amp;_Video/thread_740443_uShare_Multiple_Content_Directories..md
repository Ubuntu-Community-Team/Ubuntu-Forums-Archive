---
title: "uShare Multiple Content Directories."
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Nebetsu on 2008-03-30
So in my uShare conf, putting:

USHARE_DIR=/media/hdc1/video,/media/hdb/nebetsu/video

only lets me see the first one. How do I fix this?

---

### Post by akshtray on 2008-04-01
I have the exact same issue. I can view only the first directory set with the USHARE_DIR variable.

---

### Post by akshtray on 2008-04-01
As an update, I created a new directory and created symbolic links in it to all the other directories I wanted to access via ushare. This worked in the sense that I was able to view all the files from the centralized directory but I was unable to play any videos. It kept telling me that the file was not a valid format.

When I shared any one of those directories individually it worked great.

Thanks.

---

### Post by elwaywitvac on 2008-04-11
One option is to just add multiple directories in the command line with -c (I've only tried this with one extra dir.)

---

