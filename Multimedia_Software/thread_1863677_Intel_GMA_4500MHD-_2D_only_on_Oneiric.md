---
title: "Intel GMA 4500MHD- 2D only on Oneiric"
date: 2011-10-18
forum: Multimedia Software
---

### Post by marcmeier on 2011-10-18
Hi, All

Hoping someone can help...

I did a fresh install of Oneiric on my IBM/Lenovo R400 (7439-CTO).  I then installed ccsm and went in to change the Unity icon size- settings changed, but no icon size change.

Looked into it a bit more and found that 11.10 was defaulting to Unity 2D (I can't remember what Natty did, but I could change icon sizes, so I'm presuming I had 3D).

System Info reports "Graphics Unknown", "Driver Unknown" and "Experience Standard".  However, a Unity support test yields:

marc@marc-ThinkPad-R400:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.11

Not software rendered: yes
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: yes
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes

Unity 3D supported: yes

To me, it looks like something should be possible... but, I haven't a clue about what configuration to edit where... can someone help?

Cheers

---

### Post by BicyclerBoy on 2011-10-18
Your openGL stuff looks correct.
You can get a later version from xorg-edgers ppa.

Are you sure you don't just have to:

- logout
- select your user (do not login)
- then select unity 3d
- login with password

Does glxgears run ?
What's in the /var/log/Xorg.0.log

---

### Post by marcmeier on 2011-10-19
@BicylerBoy

Thanks for that.  Weird- after installing mesa-utils, all is sweet as.

Cheers

---

### Post by FerroPower on 2011-10-19
I was surprised to read**_ GMA 4500MHD_** because that also happen to be the name of graphic card in my laptop. but Ubuntu always detects it as GM45 while Windows detects that card as GMA 4500MHD. 

Installing latest drivers from xorg-edgers ppa rocks but at some expense like some windows games stop functioning properly in wine. I had same problem had to remove them completely to get the games working properly.

---

