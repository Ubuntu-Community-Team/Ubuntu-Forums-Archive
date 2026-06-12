---
title: "Exaile as Default: OGG-Yes / MP3-No"
date: 2011-04-10
forum: Multimedia Software
---

### Post by wmeler on 2011-04-10
In Ubuntu 10.04 LTS, I went into my home folder, Edit->Preferences under the Media tab.  I made Exaile the default Music Player.

But now I have a weird issue where when I double click on an OGG file, it opens Exaile just fine.  When I double click on an MP3 though, it opens the MP3 with Movie Player.

How do I set it such that Exaile opens MP3's automatically too?

Note:  Yes, I also tried to right click on the MP3, Open With "Other Application", and then tried to Open with Exaile (and even command line "exaile" and "exaile %F"), and unchecked and then rechecked the "Remember this application", and then Open.
I also tried restarting.  None of this helped.

---

### Post by wmeler on 2011-04-10
Solved by doing the following.

1) Right click on an individual MP3.
2) Select Properties.
3) Go to the "Open With" tab.
4) Select Exaile or if it's not there, it's at /usr/bin/exaile
5) Close.

The fix should be immediate for all MP3.

---

