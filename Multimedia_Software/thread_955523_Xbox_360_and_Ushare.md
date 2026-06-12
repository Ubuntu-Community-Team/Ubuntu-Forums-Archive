---
title: "Xbox 360 and Ushare"
date: 2008-10-22
forum: Multimedia Software
---

### Post by dschu012 on 2008-10-22
I am trying to share my media to my xbox using Ushare. I have set everything up and it seems to work fairly well. However when I am trying to share multiple folder the 2nd folder is never shared. For instance 
```
# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/My Book/Video,/media/My Book/My Music
``` In this case my music folder never was shared even though when I start ushare it says 6049 files found, which obviously is not just my videos folder.

Also another problem that doesn't seem as big is when it is sharing the videos they will appear under the videos, pictures, and music tabs in my xbox 360.

---

### Post by ilrudie on 2008-10-22
I have the same problem.  I'm not sure if its a problem with ushare or with the xbox360 but my solution was to make a ushare directory and sym link the directories I want to share into it.  Hope that helps.

---

### Post by dschu012 on 2008-10-22
That should address the first problem I was having but how would I make sure that music only shows up under music on the xbox and video only shows up under video.

Edit: Also is there a limit to the amount of songs shared to the xbox? Because only 1000 songs show up when there should be about 5k

---

### Post by ilrudie on 2008-10-23
I've never figured out how (if its possible) to stop showing videos under music.  Once again not sure where the problem really lies (xbox360 or ushare).  I don't have nearly 1000 items managed by ushare so I can't really speak on the 1,000 item limit you seem to have encountered.  If you think it might be a ushare config problem I can try to test it and see if I hit the same limit.  Let me know.

---

### Post by cj13579 on 2010-09-10
> **dschu012 said:**
> I am trying to share my media to my xbox using Ushare. I have set everything up and it seems to work fairly well. However when I am trying to share multiple folder the 2nd folder is never shared. For instance 
```
# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/My Book/Video,/media/My Book/My Music
``` In this case my music folder never was shared even though when I start ushare it says 6049 files found, which obviously is not just my videos folder.

Also another problem that doesn't seem as big is when it is sharing the videos they will appear under the videos, pictures, and music tabs in my xbox 360.

I solved the multiple shares thing by creating 1 "supershare" which was essentially a folder with a load of symlinks to the other folders that I wanted to view. I just pointed ushare to "/home/me/super".

I have the same problem with the 1000 limit for my music though. It just appears to be a load of Album art aswell but with no tracks?

---

