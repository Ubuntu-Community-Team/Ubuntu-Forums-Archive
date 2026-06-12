---
title: "Warcraft Grahical Help"
date: 2008-08-10
forum: Multimedia Software
---

### Post by GenesisV2.0 on 2008-08-10
Hi There

I have been an ubuntu user for a time and about 3 months ago purchased a dell laptop with ubuntu and upgraded it yada yada yada
 anyway heres my specs

Celeron Processor
X3100 GPU
1 gig ram

recently i tried to install world of warcraft with wine - i ran into a few problems along that way but managed to get it installed - i can log in but on the choose character screen i cant see my character and when in game i cant see my avatar and the terrain seems shadowy and in solerized bright red and orange colours - i wondered what patch or tweak i needed to make to sort this problem out once and for all - your kind of my last shot on this before i give in.

cheers for any help you can give

---

### Post by Afkpuz on 2008-08-11
I don't know the exact syntax, but you need to launch the program from the command line and add something like this to the end

```
-opengl
```

You should check around for the specific command, but I had the exact same problem and that fixed it.  Basically, tell wine to use opengl.

---

### Post by GenesisV2.0 on 2008-08-11
hi - i have added the OpenGL line to the Config.wtf file - do i still need to use the flag???

---

