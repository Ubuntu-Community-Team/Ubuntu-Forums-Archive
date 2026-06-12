---
title: "sound problem (with VirtualBox)"
date: 2009-04-13
forum: Multimedia Software
---

### Post by xkuruma on 2009-04-13
Hello all.

first of all, i wanna say that this is an amazing forum!
i've learned A LOT from this.-
but now i got a problem and don't know how to fix it.


i have ubuntu 8.10 installed, and a virtualbox machine with windows xp on it.
the thing is that... if i play music with amarok (for example), before i start the virtual machine,  when i enter windows xp, i have no sound, and cannot play any music (itunes gives me an error).
on the other hand, if i'm not playing any music in ubuntu, and i start the virtual machine, i have sound inside windows, but in ubuntu i cannot play any music (amarok just doesn't play anything)..


i hope u got any part of this x)  since it's a weird issue.

well i hope anyone can help.  thx
:)

---

### Post by Cybie257 on 2009-04-13
Best way I have found to have Audio in both HOST and GUEST is to set your audio to Pulse Audio. 

Any others, I get the same problem you get. It has something to do with sharing the resources and Pulse Audio (if I am correct on this), is more designed for multi-tasking..

-Cybie

---

### Post by xkuruma on 2009-04-13
thank youu !!!
that worked perfectly :D

thx :)

now none of the apps freezes (inside windows or not)
great!

---

