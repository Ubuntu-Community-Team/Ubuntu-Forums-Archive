---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;  ???"
date: 2012-09-04
forum: Multimedia Software
---

### Post by mips on 2012-09-04
Something is amiss and it's probably an easy fix but I'm lost here. This problem also happened with the older drivers. Some of my apps fail to work complaining about GLX issues.


12.04 AMD64, nVidia 9600GT, nvidia-current nvidia-settings v304.43


```
username@obelix:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

username@obelix:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
```

[IMG]http://ompldr.org/vZmQxMg/nv1.png[/IMG]

[IMG]http://ompldr.org/vZmQxMw/nv2.png[/IMG]

Any hints tips on how to fix this?

---

### Post by mips on 2012-09-04
Ignore this thread. I just did one of the dumbest things in my life, I did a uninstall/remove of certain components and included apt, yes apt, in the list of things to remove. 
Not gonna recover from this so I'm gonna do a 12.10 netinstall shortly, my /home is already backed up so I can just wipe / & /home

/drops head and does the walk of shame...

---

### Post by coffeecat on 2012-09-05
Closed at request of OP.

Good luck with Quantal! :)

---

