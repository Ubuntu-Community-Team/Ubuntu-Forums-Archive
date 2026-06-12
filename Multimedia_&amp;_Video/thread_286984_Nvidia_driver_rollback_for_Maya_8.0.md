---
title: "Nvidia driver rollback for Maya 8.0"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by leif3d on 2006-10-28
I updated Ubuntu Dapper to Edgy:) ...but obviously not without problems:rolleyes: ...The new Nvidia drivers 8774, don't like Maya 8.0...even though they are the supposed qualified drivers. 

I tried to install 8762 manually, but it fails to compile. I'm doing this by exiting gdm and running it through root, but nothing.  
To do this I had uninstalled Nvidia glx and changed "nvidia" to "nv" in my xorg file. but when I tried to reboot after my failed driver attempt it won't boot because of an unrecognized X error. 

Can you guys point me i the right direction? Should I reinstall 6.10 from scratch? or can I fix my current install? 

Oh, I'm also downloading Xubuntu to test it and see how it is...I just want speed and performance in the following things: Opengl,  Media player, music player and Browser. What do you guys think?

System specs:

Opteron's 285
2GB ECC
Tyan K8WE Thunder
Quadro 4500


Thanks in advance.

---

### Post by jujoje on 2006-11-12
Maya should work fine with those drivers. There is a slight bug in maya but you can fix it by following the instruction in this thread :
[http://ubuntuforums.org/showthread.php?t=272937&highlight=maya]("http://ubuntuforums.org/showthread.php?t=272937&highlight=maya")

Other than that problem it shouild work fine in edgy.

Also what problem did you get with compiling the drivers? Did you get any error messages or anything?

---

