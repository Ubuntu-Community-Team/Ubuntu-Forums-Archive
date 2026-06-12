---
title: "x264 install error"
date: 2011-01-17
forum: Multimedia Software
---

### Post by vogskis on 2011-01-17
i'm following [this tutorial]("http://ubuntuforums.org/showpost.php?p=9114176&postcount=967") to eventually install ffmpeg on my server, but i'm having issues installing x264, Step 3.

after running...

sudo checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`+`git rev-list HEAD -n 1 | head -c 7`" --backup=no --default --deldoc=yes 

here is the error message i am receiving...



Installing with make...Installing with install...



========================= Installation results ===========================

/usr/bin/installwatch: /var/tmp/tmp.SSV747Q8Dz/installscript.sh: /bin/sh: bad interpreter: Permission denied



****  Installation failed. Aborting package creation.



Cleaning up...OK



Bye.  


i think it may have something to do with some permissions modifications i made to the /var/tmp/ directory.  

anybody got an idea on what's happening here?

---

### Post by FakeOutdoorsman on 2011-01-17
I've seen this error once before when a user modified /var/tmp permissions. Start with ["bad interpreter: Permission denied" error when /var/tmp has been mounted with noexec](http://ubuntuforums.org/showthread.php?p=9614476#post9614476) and continue to the next page for a possible method of resolving this issue.

---

