---
title: "How does one view turkish writing in a music track"
date: 2011-10-05
forum: Multimedia Software
---

### Post by shantiq on 2011-10-05
How does one view turkish writing in a music track( also in general help as not sure where best)
See attached image to see what problem is


and neither will qmmp or vlc or indeed any player read these right
neither does nautilus my computer is set to english but i want to see those turkish names too


how do i do that?
Attached Thumbnails

---

### Post by vajorie on 2011-10-09
I hate this stuff (any time I play with it, I break things) but have a look at your locale settings. Afaik, you need to set it up to have UTF8. Here's my settings (I can see Turkish chars in file names fine).

```

$ locale #this is the command you run to get info from system
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

This link might be of use: [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

