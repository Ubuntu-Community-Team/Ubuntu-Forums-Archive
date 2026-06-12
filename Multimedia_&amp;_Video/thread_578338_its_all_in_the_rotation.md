---
title: "its all in the rotation"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by leovA on 2007-10-17
hey all,

i need to invert my screen, because i am using a beamer wich hangs from the ceiling upside down, and doesnt have an integrated rotate function.

i tried adding 

```
Option "rotate" "inverted"
```

in xorg.conf, everything is now inverted but when i try to start mythtv i get an segmentation fault (core dumped)

when i remove the line in xorg.conf it start op no problem, so i was wondering do any of you know how i can invert my screen and still have mythtv working? its rather important to me and ive been searching for 3 days now :(

i am using feisty, any help is greatly appreciated :KS

---

### Post by samba on 2007-10-19
Hi,

I have a Toshiba Portege M405 tablet pc. I just installed ubuntu 7.10, and screen rotation doesn't work anymore. I previously used Metacity and created a script as above to enable screen rotation and rotate the pen as well. Everything worked fine. But now, when I type say

xrandr -o left

the screen kind of rotates (but doesn't resize itself) and nothing works anymore; i mean, i can still move the cursor, but I can't input anything anymore. I suppose the problem is probably with Compiz since I just migrated from Metacity. My video card driver is i810.

Anyone else has this problem, or better, a solution? ;-)

cheers
vincent

---

