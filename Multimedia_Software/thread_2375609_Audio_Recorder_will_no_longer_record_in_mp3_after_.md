---
title: "Audio Recorder will no longer record in mp3 after uprgade to 17.10"
date: 2017-10-25
forum: Multimedia Software
---

### Post by WillEllen on 2017-10-25
Audio Recorder v. 2.0.2 records in all other formats but if mp3 is selected nothing happens.  Verified that lame, all the gstreamers 1.0, lubuntu-restricted-addons (also extras) and ubuntu-restricted-addons (also extras) are installed.  Re-installed the older version (1.9.7); still no work.  Help!

---

### Post by Yellow Pasque on 2017-10-26
If you run it from the terminal and try to record an mp3, do you get any error messages that may give a clue?

---

### Post by WillEllen on 2017-10-26
SOLVED
Terminal said "to support mp3 format you should install Gstreamer-plugins for id3mux".  I had the good, the bad but not the ugly.  When installed it now records in mp3.  Thanks much.

---

