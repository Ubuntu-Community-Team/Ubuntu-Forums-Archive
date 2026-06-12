---
title: "Can I make my own Nautilus mencoder script??"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by s1mple_M4N on 2007-01-31
Hi all - I started using the recordmydesktop app to make ogg movies and found a terminal mencoder command to convert those ogg movies to avi. All is good so far.

What I was wondering is - is it possible for me to create a script for Nautilus Scripts that would have this terminal command??

I have been using Ubuntu for only 6 months, and my Linux knowledge is based on following instructions from these excellent forums and some good GUI apps. I would really appreciate help on this one.

Thanks in advance,

RoyJ

---

### Post by Bossieman on 2007-01-31
This is really easy. 
Find the file, rightklick on the out.ogg file and choose scripts and then "convert to avi"

just put this into a file named "convert to avi" and put the file in home/USERNAME/.gnome2/nautilus-scripts/

#!/bin/bash
#

mencoder -idx out.ogg -ovc lavc -oac mp3lame -o out.avi

---

### Post by s1mple_M4N on 2007-01-31
Bossieman, you are a legend!! Thanks a million for that.

RoyJ

---

