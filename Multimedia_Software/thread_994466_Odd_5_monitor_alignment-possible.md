---
title: "Odd 5 monitor alignment-possible?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by Mattventura on 2008-11-26
I have decided to go for a 5 monitor setup on my new build. I have 2 old monitors and I will be getting 3 new ones. However, due to space constraints, the only way I can do this is to have 3 monitors on one level and 2 above. However, from my experience of writing xorg.conf files, it is only possible to specify a strict direction such as "leftof" or "rightof". Is it possible to configure the monitors in such a way that they will not be aligned?

What I mean by this is that the monitors will be placed like this:

```

          _________   _________
         |         | |         |
         |1280x1024| |1280x1024|
         |_________| |_________|
 ___________   ___________   ___________
|           | |           | |           |
| 1680x1050 | | 1680x1050 | | 1680x1050 |
|           | |           | |           |
|___________| |___________| |___________|


``` 

FYI, I will be using two ATI cards (one with 4 DVI ports) for this. Is it possible to align the monitors like this?

---

