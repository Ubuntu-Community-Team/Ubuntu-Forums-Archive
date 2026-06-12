---
title: "K3B can't find LAME"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by daschmidty on 2007-05-29
I am trying to use K3B to rip an audio cd to mp3. I have libk3b2-mp3 and the latest Lame package installed. I get no error message regarding burning mp3's that works fine. But if i go to rip a track, there is no option to use the lame encoder that appears as the solution on all the other threads. Also, the plugins screen for k3b does not show the lame plugin as installed, even though I have lame. I have tried both the ubuntu and medibuntu k3b packages and neither seems to work. Is there some setting I need to change to make this work?

---

### Post by daschmidty on 2007-05-29
solved the problem by adding 
lame -h --tt %t --ta %a --tl %m --ty %y --tc %c - %f

to the external encoder plugin

---

### Post by daschmidty on 2007-05-29
well this is great except Amarok won't play the files...says media could not be loaded, though all my other mp3's work, and they will play in vlc just fine.

---

