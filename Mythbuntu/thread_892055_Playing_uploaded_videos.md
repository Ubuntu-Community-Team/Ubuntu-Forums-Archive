---
title: "Playing uploaded videos"
date: 2008-08-16
forum: Mythbuntu
---

### Post by Gorf on 2008-08-16
Perhaps I am totally missing this in the documentation, but if I have collection of videos in avi or mpeg, can't I upload them to my MythTV box and watch them?  I thought I understood that I could upload to /var/lib/mythtv/videos and then they would appear in the video browser within the MythTV interface.  Is this not right?

---

### Post by zdude on 2008-08-16
> **Gorf said:**
> Perhaps I am totally missing this in the documentation, but if I have collection of videos in avi or mpeg, can't I upload them to my MythTV box and watch them?  I thought I understood that I could upload to /var/lib/mythtv/videos and then they would appear in the video browser within the MythTV interface.  Is this not right?

You need to run the video manager so it finds the files.

---

### Post by newlinux on 2008-08-17
Instead of copying them over the /var/lib/mythtv/videos you could also just change (or add a directory) to where mythvideo looks for files to include the location where you already have the videos.

---

### Post by Loaded.len on 2008-08-17
If you've already got them in you default storage group, then zdude's right, just gotta open up video manager and that alone with scan the newly added files... and, as long as you're in there, you may want to edit metadata, search imdb, etc... However, if you don't care about metadata and you just want files to show up immediately in your video browser, there are a couple settings to look at.

Utilities/Setup / Media Settings / Video Settings / General
Page 2/7
there are 3 items to look at (depending on your default view (Browser, Gallery, or List)
* Video Browser browses files
* Video Gallery browses files
* Video List browses files

selecting all of these, or the one you use by default will allow you to view them as soon as they hit the directory and not have to scan them.

---

