---
title: "[X11 problem?] x11grab on other display"
date: 2011-08-05
forum: Multimedia Software
---

### Post by mp3butcher on 2011-08-05
Hello 
I have a lot of passive screencast to do so (record a 3D application visual results) so i would like to do it on an other display than my working :0.0 on vt7.
I have tested a lot of stuff with 2 different user accounts and  
[PHP]ffmpeg -f x11grab -i :1.0 - s cif  capture.mpg[/PHP]

but when i swap between my working display :0.0 (on vt7 ) and my recording display :1.0(on vt8 ) , it seems that X stops to refresh and the captured frames freeze (still captured but not refreshed)...
(As all my walkaround for this fails, consider my config file for kde and xorg as defaut ones)

Is there an easy way to tell X not to stop refreshing a display (in my case :1) when swapping between others terminals?
I've tried to startx with different options and xorg.conf without any success..
Thanks by advance
(I don't know if my hardware configuration can help : QuadCore Intel Q8300 + 1GPU Nvidia GTX 275+1screen)

---

