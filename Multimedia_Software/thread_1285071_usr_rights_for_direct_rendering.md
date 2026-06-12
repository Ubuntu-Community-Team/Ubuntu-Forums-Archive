---
title: "usr rights for direct rendering"
date: 2009-10-07
forum: Multimedia Software
---

### Post by rkg on 2009-10-07
Hello,

I'm a newbie using Ubuntu JJ and I've a similar problem with direct rendering than some guys in other threads, however I found no solution to my problem. When I run "glxinfo | grep direct" I get following message:
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

However, when I run it as sudo, direct rendering is enabled and also the glxgears are working, so I would like to enable direct rendering for my usr account. I've no xserver-xgl installed, and the xorg.conf is allready extended by:

```
Section "Module"   
    load "dri" 
    load "glx" 
EndSection         

Section "Dri"      
    Mode 0666  
EndSection   

```

I have an Intel chipset Q45 with onboard graphics in my PC. glxinfo tells me, that the OpenGL renderer string is:>  Mesa DRI Interl (R) Q45/Q43 GEM 20090326 2009Q1 RC2 x86/MMX/SSe2

I really appreciate help. Thx in advance.

---

### Post by rkg on 2009-10-07
I noticed, that when I turn of the visual effects in the appearance setting, the problem is solved. Interesting...

---

