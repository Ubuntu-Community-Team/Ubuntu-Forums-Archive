---
title: "pulse audio and 5.1"
date: 2008-10-16
forum: Multimedia Software
---

### Post by nimeshchandran on 2008-10-16
hello guys i just installed ubuntu do that now i have a dual boot system with xp as the other os.. the thing is i am getting sound from all my speakers including the subwoofer.. i am using pulseaudio.. but thing is the center + lfe is swapped with the surround speakers.. i checked through by using the command 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

and center and lfe is exchangedwith surround...

but the funny thing is in volume control everything is working as it is meant to be.. if i lower the volume of lfe then lfe volume responds as it should... 

so what shall i do guys..

---

### Post by markbuntu on 2008-10-16
You need to remap the speaker outputs, there is a guide to doing that here:


[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

