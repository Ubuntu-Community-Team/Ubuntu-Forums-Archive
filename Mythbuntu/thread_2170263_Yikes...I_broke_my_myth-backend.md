---
title: "Yikes...I broke my myth-backend"
date: 2013-08-25
forum: Mythbuntu
---

### Post by donb21 on 2013-08-25
Just did a fresh install of Mythbuntu 12.04...all was working great.  I used the mythbuntu control panel to activate all the plugins, which appeared to work.  Then rebooted and the backend would not start.  Checked the mythbackend logs and see these messages.  It looks like I need to re-install something...any idea which?



Aug 25 13:40:08 nick mythbackend[2510]: C CoreContext mythcorecontext.cpp:195 (Init) Application binary version (0.25.20120506-1) does not match libraries (0.25.20130225-1)
Aug 25 13:40:08 nick mythbackend[2510]: W CoreContext mythcorecontext.cpp:201 (Init) This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
Aug 25 13:40:08 nick mythbackend[2510]: ! CoreContext mythcontext.cpp:1031 (MythContext) MythContext: Unable to allocate MythCoreContext
Aug 25 13:40:08 nick mythbackend[2510]: ! CoreContext mythcontext.cpp:1052 (Init) Application binary version (0.25.20120506-1) does not match libraries (0.25.20130225-1)
Aug 25 13:40:08 nick mythbackend[2510]: W CoreContext mythcontext.cpp:1062 (Init) This application is not compatible with the installed MythTV libraries.
Aug 25 13:40:08 nick mythbackend[2510]: C CoreContext main.cpp:108 (main) Failed to init MythContext.

---

### Post by donb21 on 2013-08-25
I posted this problem on the myth-user mail list.  All I had to do was a simple upgrade:

> You need to update the rest of your packages. Do a "sudo apt-get update && sudo apt-get upgrade"

That fixed it.  I also re-installed the plugins manually:

don@nick:~$ sudo apt-get install mythweb
don@nick:~$ sudo apt-get install mythweb
don@nick:~$ sudo apt-get install mythweather
don@nick:~$ sudo apt-get install mythnews
don@nick:~$ sudo apt-get install mythnetvision
don@nick:~$ sudo apt-get install mythmusic
don@nick:~$ sudo apt-get install mythgame
don@nick:~$ sudo apt-get install mythgallery
don@nick:~$ sudo apt-get install mythbrowser
don@nick:~$ sudo apt-get install mytharchive

---

