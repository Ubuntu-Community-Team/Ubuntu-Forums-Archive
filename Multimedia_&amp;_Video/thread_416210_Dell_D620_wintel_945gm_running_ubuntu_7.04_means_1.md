---
title: "Dell D620 w/intel 945gm running ubuntu 7.04 means 1024 x 768 res?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by berserkerror08 on 2007-04-20
I have a Dell D620 running the latest ubuntu. no matter what i do, it sticks to 1024 x 768 or lower. the native is 1200 X 768. ive tried all sorts of tutorials and guides but i always end up having to reinstall ubuntu because i get error messages when i start up halting the boot. 

p.s. i have intel 945gml. everything else works great but not the res. if i change to vesa using that reconfig tool in terminal, i get the res, but lose those neat desktop effects and i still wanna try beryl.


HELP!

---

### Post by NilsE on 2007-04-21
Which model D620 do you have.  Mine is native 1440x900 with the 945GM

Anyway give 915resolution a try.  Go into terminal and enter

sudo 915resolution -l 

From the list it generates pick  a mode from the list.  Probably 5c works best

Then enter

sudo 915resolution 5c xxxx yyyy 24  

where xxxx and yyyy = the resolution you want

Then restart the xserver.

You may want to also search for auto915resolution and use that to set the resolution at boot every time since 915resolution alone is not persistent.

---

