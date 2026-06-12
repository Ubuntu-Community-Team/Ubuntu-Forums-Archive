---
title: "3d apps seem to not work"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by jorik42 on 2008-02-26
whenever i open a 3d modeling application (blender, wings3d, ect), the application viewport flickers on and off constantly and rapidly, making the program unusable.  does anyone have any ideas as to how to fix this problem?

thanks, 
     jorik

---

### Post by luisromangz on 2008-02-26
What kind of video card do you use? Have you properly configured the drivers for it?

---

### Post by xeth_delta on 2008-02-26
> **jorik42 said:**
> whenever i open a 3d modeling application (blender, wings3d, ect), the application viewport flickers on and off constantly and rapidly, making the program unusable.  does anyone have any ideas as to how to fix this problem?

thanks, 
     jorik

Are you using compiz-fusion/beryl? AFAIK OpenGL applications will currently give you strange behaviour under compiz. Please, correct me if I am wrong. You can switch to the regular window manager while using OpenGL programs.

---

### Post by jorik42 on 2008-02-26
as for video cards, i use an ATI radeon hd 2600, and i believe that the drivers are set up for it; at the very least i am now able to utilize compiz (which i was unable to previously).  what would be the best way to ascertain if the drivers are correctly set up?

also, thanks for the tip concerning compiz/opengl usage.  ill look into that and see if it makes a difference.  

jorik

---

### Post by xeth_delta on 2008-02-26
> **jorik42 said:**
> as for video cards, i use an ATI radeon hd 2600, and i believe that the drivers are set up for it; at the very least i am now able to utilize compiz (which i was unable to previously).  what would be the best way to ascertain if the drivers are correctly set up?

also, thanks for the tip concerning compiz/opengl usage.  ill look into that and see if it makes a difference.  

jorik

It should make a difference for the flickering. When I was using beryl (back in the Feisty Fawn days), I could not even start FlightGear with it enabled.
Right now, if I want to avoid the flickering and I don't want to switch to kwin, I just make sure all other windows besides FlightGear are minimized.

---

### Post by jorik42 on 2008-03-01
thanks; the idea of disabling compiz/beryl did indeed solve the issue.  however, its a bit of a pain to have to turn it off and on all the time.  also, minimizing all the windows doesnt seem to help..  is there a way to have both compiz/beryl and some 3d/openGL application running at once?  

any ideas would be appreciated
   thanks
      jorik

---

### Post by xeth_delta on 2008-03-02
> **jorik42 said:**
> thanks; the idea of disabling compiz/beryl did indeed solve the issue.  however, its a bit of a pain to have to turn it off and on all the time.  also, minimizing all the windows doesnt seem to help..  is there a way to have both compiz/beryl and some 3d/openGL application running at once?  

any ideas would be appreciated
   thanks
      jorik

Hmm, for me it is not that difficult to switch since I have "Compiz Fusion Icon" installed. It is then just a matter of selecting which window manager I want to use on the fly. Search for "Compiz Fusion Icon" and if you need help, just ask.

Minimizing all other windows seems to reduce almost all flickering for me, but I suppose it depends from system to system.

---

