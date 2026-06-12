---
title: "iPlayer needs sudo?"
date: 2009-09-05
forum: Multimedia Software
---

### Post by Steve.the.Goolie on 2009-09-05
Hi all,

I'm using Ubuntu 8.04 and have had no problems with BBC iPlayer until about three days ago.
All I get now is a black square where the picture is supposed to be and nothing loads.
I have tried uninstall / reinstall but to no effect.
Flash works fine.

I have not installed any other applications recently, only Ubuntu updates.

In desperation, I started Firefox from the Terminal with *gksudo* and iPlayer then works fine, but I don't really want to run Firefox with administrative privileges all the time.

Is there anything I can do? or do I just have to accept the situation?

Steve

---

### Post by redjam on 2009-09-27
I have exactly the same problem.

Just installed Xubntu. Installed Flash plugin. iPlayer works fine, just like that.

Had a problem with DVDs playing so I messed about with some other stuff - installed some different plugins etc. Now when I try to play a video on iPlayer I get a black screen - not even any error message - just plain old blank screen :confused:

If I start Firefox with sudo access, it works fine.

Anyone know what could be causing this? Have since removed all plugins and reinstalled various different ones.

---

### Post by Steve.the.Goolie on 2009-09-28
Well, it turned out the solution was embarrassingly simple for me, I opened Firefox, went to [TOOLS > Clear Private Data] and cleared the cache. Now Iplayer works fine!
Must have been them pesky Aliens messin up my computer again :confused:

Steve

---

### Post by redjam on 2009-09-28
Haha oh yeah, forgot to reply... I just deleted my Firefox profile in /.mozilla and that sorted it :)

Thanks for replying.

---

