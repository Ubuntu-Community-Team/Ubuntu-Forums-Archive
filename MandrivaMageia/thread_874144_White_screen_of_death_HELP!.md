---
title: "White screen of death??? HELP!"
date: 2008-07-29
forum: Mandriva/Mageia
---

### Post by Fzang on 2008-07-29
Alright, I just installed mandriva on my other computer and it works just fine, but now I some logout/hard reset weird thing and turned off the computer...

Now when I turn it back on there's only a white screen of death staring at me

What do I do, and what did I do wrong?

---

### Post by Fzang on 2008-07-29
Alright, seems like I've found the problem

There's some sort of bug if you flip on the "xgl" (I think that's the name?) instead of "Native support" (yet again, I'm guessing names because I'm unable to boot mandriva)

So, the xgl switch is a bad bad idea it seems.... now how do I turn it back to native support or whatever when I can't even boot mandriva?

EDIT: xgl -_-

---

### Post by AdamWill on 2008-07-30
It's Xgl.

If you hit ctrl-alt-F1 you should get to a console login screen. Log in as root and run 'drak3d' - you can disable 3D effects there, then when you restart, the graphical desktop should be working again. Then you can re-enabled 3D effects with the working setting, if you like. :)

---

### Post by Fzang on 2008-07-30
Thanks! :D

you should put a warning sticker on that switch or something >_>

---

### Post by AdamWill on 2008-07-30
Well, it shouldn't really *do* that. :) Sounds like a driver bug.

What graphics card is this?

---

### Post by Fzang on 2008-07-31
It's an NVidia card which mandriva calls "C51 [GeForce 6150 LE]"

---

### Post by wxnker on 2008-08-04
I have Nvidia GF6150 graphics as well. XGL doesn't work well with that. Like you already discovered, It should be used with "native".

---

