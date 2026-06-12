---
title: "projectM-pulseaudio error after updates"
date: 2008-05-18
forum: Multimedia Software
---

### Post by denham2010 on 2008-05-18
Hi, hoping someone can help here. 
 
Last night I installed ProjectM from SVN, following the guide in this post.

[http://ubuntuforums.org/showthread.php?t=749793](http://ubuntuforums.org/showthread.php?t=749793)
 
All worked perfectly and I had a fully functioning ProjectM. 
 
 
This morning, there were some updates for my system (running Xubuntu 8.04). The following files were updated: 
 
```
Commit Log for Sun May 18 08:43:28 2008 
 
Upgraded the following packages: 
gdm (2.20.5-0ubuntu3) to 2.20.6-0ubuntu1 
libglib2.0-0 (2.16.3-1) to 2.16.3-1ubuntu1 
libglib2.0-data (2.16.3-1) to 2.16.3-1ubuntu1 
libglib2.0-dev (2.16.3-1) to 2.16.3-1ubuntu1 
libgphoto2-2 (2.4.0-8ubuntu6) to 2.4.0-8ubuntu7 
libgphoto2-port0 (2.4.0-8ubuntu6) to 2.4.0-8ubuntu7 
libnautilus-extension1 (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6 
libtotem-plparser10 (2.22.2-0ubuntu1) to 2.22.3-0ubuntu2 
nautilus (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6 
nautilus-data (1:2.22.2-0ubuntu5) to 1:2.22.2-0ubuntu6
```
 
Since the updates, I am getting the following problem whenever I try to launch projectM-pulseaudio: 
 
```
:~$ projectM-pulseaudio  
dir:/usr/share/projectM/config.inp  
reading ~/.projectM/config.inp  
configFile: ~/.projectM/config.inp 
MAX SAMPLES:2048 
configFile: ~/.projectM/config.inp 
MAX SAMPLES:2048 
Failed to insert builtin function "int" into collection! Bailing... 
Aborted
```
 
Thinking something had just been broken between the original configuring and installing of ProjectM and the updates, I fully removed ProjectM and re-installed from SVN this morning (zero errors during ccmake, make and make install). 
 
Unfortunately, I am still getting the same error. 
 
All help is greatly appreciated, I have been looking for a visualiser for quite some time that doesn't slow my system to a crawl, and after using ProjectM last night, it fit's the bill perfectly!

(I have also posted this on the ProjectM sourceforge forum to try and cover both bases!)
 
Thanks.

*** UPDATE ***

Ok, I tried fully removing ProjectM, and then downgrading the packages that were previously updated, as these were the only changes that occurred between ProjectM working and failing.

I then re-installed ProjectM, and I'm still getting the same error.....it's rather frustrating as it was working perfectly until these updates, and now it just refuses to work.

Any ideas? I would really like to get this one solved!

Thanks.

---

### Post by denham2010 on 2008-05-18
*** SOLVED ***

After figuring out how to debug from reading other posts, I found ProjectM was looking for a saved playlist, which no longer existed.

From this, I eventually found that not only does ProjectM create a ~/.projectM folder for your settings, it also creates a ~/.config/ProjectM folder, which happens to store the deafult playlist to look for upon opening.

Since the playlist no longer existed, ProjectM would no longer start.

Deleting my ~/.projectM and ~/.config/ProjectM folders and then restarting solved the issue.

---

### Post by adam_kimber on 2008-08-22
Thank you :D

---

### Post by ankle on 2008-08-25
Thanks for posting this, I had the same problem today.

---

### Post by struktured on 2008-09-18
My bad, really got to address that bug.

- struk

---

### Post by nonanano on 2009-12-19
Yep deleting the ~/.projectM folder magically fixed this issue. Cheers mate. :)

---

### Post by CCC999 on 2010-01-03
denham many thanks - I had a similar experience. Likely some other install prompted a 'clean-up' of old packages that broke ProjectM (upgrade to Karmic). Tried all the tricks with no luck until I found this thread. My only difference was the capital P in the second directory that needed removal (mine was lower case):
1) ~/.projectM and
2) ~/.config/projectM 

Thanks again!

---

