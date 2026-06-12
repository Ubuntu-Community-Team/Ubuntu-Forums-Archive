---
title: "VLC without interface, faster video listing?"
date: 2008-03-14
forum: Mythbuntu
---

### Post by Akegata on 2008-03-14
I'm starting to get mythbuntu set up just like I want (except that browsing for video files is still a bit awkward), but I still have two issues:

1. Is there any way to stop VLC from showing the interface at startup? It's pretty annoying to see it pop up and a cursor appear on the screen for a few seconds whenever a video is started.

2. Can you somehow make mythtv browse files on the harddrive on the fly instead of searching through the whole video folder every time you go to the video browser?
It takes almost a minute for mythtv to show up the videos when I go to "Watch Videos", I assume this is because it scans the whole folder (plus it doesn't re-read changes I make in the folders until I go out of the video browser and then go back in). That's..extremely annoying, actually. :/

---

### Post by Akegata on 2008-03-14
I just found out how to get rid of the interface; simple: add -I dummy to the VLC command line. That still doesn't get rid of the cursor though..
And more importantly, it still takes forever before I can browse files to play. :/

---

