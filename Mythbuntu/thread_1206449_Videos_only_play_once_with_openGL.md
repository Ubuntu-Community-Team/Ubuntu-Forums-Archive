---
title: "Videos only play once with openGL"
date: 2009-07-07
forum: Mythbuntu
---

### Post by bergqvistjl on 2009-07-07
hi, whenever i try and play something (liveTV or recordings) on mythtv, using openGL (I want to use this as i get a higher-res OSD), the first time, it plays fine. However, when i stop playing, and then play a video again (can be the same one, or a different one), i get no video, just a black screen with the audio (the remote works fine, i can change channels etc, just no video). This lasts until i quit the frontend, and restart it, then i can play again fine, just only the 1st time. i'm using Nvidia proprietry drivers version 180, and ubuntu 9.04 x64 (with mythbuntu added onto it via the metapackage). I found a solution, which i think works on here: 
[http://www.nvnews.net/vbulletin/showthread.php?t=111308](http://www.nvnews.net/vbulletin/showthread.php?t=111308)

but, its confusing, what with all the different patches, which anyway i dont know how to install them. I have enabled the mythtv fixes repository like the site said. btw, video plays back fine with no problems while using XV, however i really want to use OpenGL. Any ideas?

---

### Post by bergqvistjl on 2009-07-07
any ideas? i think if i could compile a couple of patches, it would be fine, but i dont know how. the location that's mentioned in the diff file does not exist on my PC!

---

### Post by jyavenard on 2009-07-07
There is a bug in OpenGL (and it's been there for a while) when using OpenGL 1.3 (first described here: [http://www.nvnews.net/vbulletin/showthread.php?t=111308](http://www.nvnews.net/vbulletin/showthread.php?t=111308))

You need to force the use of OpenGL 1.2..

There are various solutions, either compile it yourself and install one of those patches.

A work around is:
Index: libs/libmythtv/util-opengl.cpp
===================================================================
--- libs/libmythtv/util-opengl.cpp	(revision 17061)
+++ libs/libmythtv/util-opengl.cpp	(working copy)
@@ -102,6 +102,9 @@
     if (!ret)
         return false;
 
+    if (gl_minor > 2)
+        gl_minor = 2;
+
     static_major = major = gl_major;
     static_minor = minor = gl_minor;
     static_ret = true;

 
A better fix is using Mark Kendall OpenGL mod:
[http://www.btinternet.com/~mark_kendall](http://www.btinternet.com/~mark_kendall)

Or my VDPAU patches (which also adds a lot of improvement with OpenGL)
[http://www.avenard.org/media/MythTV_%26_VDPAU/Entries/2009/6/28_Patch_20744.html](http://www.avenard.org/media/MythTV_%26_VDPAU/Entries/2009/6/28_Patch_20744.html)

Or if you don't want to recompile yourself, you can use this repository
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by bergqvistjl on 2009-07-07
im using the repository. ill tell you how it goes.

---

### Post by bergqvistjl on 2009-07-07
It worked! thank you so much. Although the mythbackend update failed to install i think due to wrong/missing dependencies. Doesnt seemed to have caused a problem however.

---

