---
title: "Certain HD-PVR recordings aren't playing back"
date: 2013-12-17
forum: Mythbuntu
---

### Post by davefor2 on 2013-12-17
I have 12.04.3 Myth frontend/Backend

I updated to .27 from .25 and now I have a problem with Play back of some recording recorded from
my HDPVR. If you select the recording you will get the Please Wait screen and then it will flash the recording and then kick
back to the recordings menu.
I have a HDHOMERUN Prime also and plays back fine. After some searching I found a possible solution on
mythtv.org/trac/ticket/11882 
It looks like I need to edit the H264Parser.cpp and the path is mythtv/libs/libmythtv/mpeg/H264Parser.cpp

My question is I can't find this path does anyone no where to find this file. The file manager thunar doesn't
have a search.

Thanks

---

### Post by khPWXxF on 2013-12-18
Can you find a common factor for the files which do not play?
eg Is it only those recorded before the upgrade?, only those after?, from a particular channel?

As for finding the file, try the locate command (google or man for info) from a terminal session.
It will only find files you have permissions for so you may need to sudo it.
Another find command to look at is 'find'

Phil

---

