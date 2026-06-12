---
title: "Upgrade to 10.04 broke my 3d"
date: 2010-06-02
forum: Multimedia Software
---

### Post by bwisdom on 2010-06-02
Ok so I was using 9.10 and I had to do quite a bit of working to get World of warcraft to work. Then 10.04 rolls around and I decide to try it out. The problem is now that I have no 3d rendering anymore. To check I did this

bwisdom@crayon:~$ glxinfo | grep rendering
bwisdom@crayon:~$ 

As you can see there, nothing is returned when I type this out. Im not sure what to do because even in 9.10 it always said yes and it said yes before I upgraded. Now I dont even get a no.

I am victim of the dreaded Intel 8280 chipset and my graphics card is ATI Inc M71 [Mobility Radeon X2100]

EDIT: After posting I thought this would help, maybe not but im editing it in anyway.

bwisdom@crayon:~$ glxinfo
name of display: :0.0
Segmentation fault

---

