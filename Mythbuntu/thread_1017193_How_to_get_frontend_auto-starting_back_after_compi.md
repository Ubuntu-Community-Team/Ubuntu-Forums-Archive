---
title: "How to get frontend auto-starting back after compile?"
date: 2008-12-20
forum: Mythbuntu
---

### Post by zoiks on 2008-12-20
OK, I'll try to keep the story short...

I have checked out and compiled 0.21-fixes rev 19401. I applied three patches to get the Hauppauge HDPVR to run on it. I have compiled and installed mythtv (but not yet mythplugins). I copied the newly compiled executables from /usr/local/bin (where the mythtv make scripts put them by default) to /usr/bin, where mythbuntu puts them.

Unfortunately, now, mythfrontend won't autostart when the system boots, and I can't figure out how to do it. The backend starts just fine, and I can start mythfrontend from the user that is auto logged in, though many of the settings are messed up (like the theme) because this user is not mythtv. (If I su to mythtv, it won't connect to the X server.)

So the question is, [I]**how do I get the system set up again so that mythfrontend will start on boot, and be started as the mythtv user?**
[/I]
Any help is greatly appreciated!

(FWIW, some added information: the compiled version of mythtv I have now, based on fixes, does in fact work with the HDPVR. There are a few glitches, and I'm trying to fix them one by one, but it is functional. Also, MythControlCenter doesn't work anymore, but I suppose I could get by without it.)

---

