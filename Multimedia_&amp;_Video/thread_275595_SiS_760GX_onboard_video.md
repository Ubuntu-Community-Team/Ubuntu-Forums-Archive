---
title: "SiS 760GX onboard video"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by Locomotion on 2006-10-11
Hello. :cool: 

I have a 760GX-M mainboard and when I try to open some games, it shows a error:

> Couldn't find matching GLX visual

I looked about that mainboard, but got very confused with those technical terms (english is not my 1st language)!

So, can someone say if I can play those games?

---

### Post by Locomotion on 2006-10-11
nothing? :(

---

### Post by John.Michael.Kane on 2006-10-11
This error **[Couldn't find matching GLX visual]** means the program you used tried to use a GLX visual that was not available on that X server. the color depth might be set to high for the GPU you have.

This is just a guess since i have never experienced that error. you could try changing the color depth.

---

### Post by Locomotion on 2006-10-11
hm
I think is because my video board is not configured...

Theres a command to see if GLX is actived, but I cant remember ](*,) 

When I execute it, it says that GLX is off! :(

---

### Post by John.Michael.Kane on 2006-10-11
For the most part from what i understand theres no 3d support for sis under linux.

You can tryo to run **glxinfo** it should tell you if you have **direct rendering:yes/no**

---

### Post by Locomotion on 2006-10-12
> locomotion@locomotion-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
...

:(

---

